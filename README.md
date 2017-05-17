# 001Two-Sum
今天正式记录Leetcode题目思路，否则过两天就忘记。

Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

给一个数组找出两个书之和是target数。
可以暴力解法nxn，但肯定超时。

用一个hashmap记录数组，然后遍历一边数组即可，时间复杂度n。

代码如下：
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        //看了讨论区的代码，写的真标准啊
        Map<Integer, Integer> map = new HashMap<>();
        
        for(int i = 0; i < nums.length; i++){
            map.put(nums[i], i);
        }
        
        for(int i = 0; i < nums.length; i++){
            int complement = target - nums[i];
            //附加条件防止出现 6 [3,2,4] 3的时候自身重复情况
            if(map.containsKey(complement) && map.get(complement) != i){
                return new int[] { i, map.get(complement)};
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
