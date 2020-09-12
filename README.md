# MergeSort

``````C#
class Program
    {
        static void Main(string[] args)
        {
            int[] arr = { 23, 9, 18, 32, 61, 50, 4, 99, 3, 1, 555 , 0};
            for (int i = 0; i < arr.Length; i++)
            {
                Console.Write(arr[i] + " ");
            }
            Console.WriteLine();

            List<int> input = new List<int>();
            for(int i=0; i<arr.Length; i++)
            {
                input.Add(arr[i]);
            }

            var result = MergeSort(input);
            for(int i=0; i<result.Count; i++)
            {
                Console.Write(result[i] + " ");
            }

            Console.ReadLine();
        } 

        public static List<int> MergeSort(List<int> input)
        {
            if (input.Count <= 1) return input;

            var left = new List<int>();
            var right = new List<int>();

            int middle = input.Count / 2;

            for(int i=0; i<middle; i++)
            {
                left.Add(input[i]);
            }
            for(int i=middle; i<input.Count; i++)
            {
                right.Add(input[i]);
            }

            left = MergeSort(left);
            right = MergeSort(right);

            return Merge(left, right); 
        }

        public static List<int> Merge(List<int> left, List<int> right)
        {
            var result = new List<int>();

            while(left.Count > 0 || right.Count > 0)
            {
                if(left.Count > 0 && right.Count > 0)//if it matches, it will not go next element
                {
                    if(left.First() <= right.First())
                    {
                        result.Add(left.First());
                        left.Remove(left.First());
                    }
                    else
                    {
                        result.Add(right.First());
                        right.Remove(right.First());
                    } 
                }
                else if (left.Count > 0)
                {
                    result.Add(left.First());
                    left.Remove(left.First());
                }
                else if(right.Count > 0)
                {
                    result.Add(right.First());
                    right.Remove(right.First());
                }
            }

            return result;   
        }
    } 


``````
