1022. Sum of Root To Leaf Binary Numbers

Given a binary tree, each node has value 0 or 1.  Each root-to-leaf path represents a binary number starting with the most significant bit.  For example, if the path is 0 -> 1 -> 1 -> 0 -> 1, then this could represent 01101 in binary, which is 13.
For all leaves in the tree, consider the numbers represented by the path from the root to that leaf.
Return the sum of these numbers.

###### Example 1:
![image](https://assets.leetcode.com/uploads/2019/04/04/sum-of-root-to-leaf-binary-numbers.png)
```
Input: [1,0,1,0,1,0,1]
Output: 22
Explanation: (100) + (101) + (110) + (111) = 4 + 5 + 6 + 7 = 22
```
##### Note:

* The number of nodes in the tree is between 1 and 1000.
* node.val is 0 or 1.
* The answer will not exceed 2<sup>31</sup> - 1.

---
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var sumRootToLeaf = function(root) {
  let prefix = 0;
  const ans = [];
  helper(prefix, root, ans);
  return ans.reduce((a, b) => a + b);
};

function helper(prefix, node, arr) {
  if(!node) return;
  const num = prefix * 2 + node.val;
  if(!node.left && !node.right) {
    arr.push(num);
    return;
  }
  helper(num, node.left, arr);
  helper(num, node.right, arr);
}
```
