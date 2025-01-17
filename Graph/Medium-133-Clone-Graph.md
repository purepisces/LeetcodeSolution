dfs return the copied node, for oldToNew's dictionary, key is the old node, and value is the new node.
```python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""

class Solution(object):
    def cloneGraph(self, node):
        """
        :type node: Node
        :rtype: Node
        """
        oldToNew = {}

        def dfs(node):
            if node in oldToNew:
                return oldToNew[node]

            copy = Node(node.val)
            oldToNew[node] = copy
            for nei in node.neighbors:
                copy.neighbors.append(dfs(nei))
            return copy

        return dfs(node) if node else None
```

Time Complexity: O(V+E)

Space Complexity: O(V)

Where V is the number of vertices and E is the number of edges.
___
My bad solution:

I should make dfs to return the copied node.
```python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""

class Solution(object):
    def cloneGraph(self, node):
        """
        :type node: Node
        :rtype: Node
        """
        if not node:
            return []
        OldtoNew = {}
        def dfs(node):
            if node in OldtoNew:
                return
            OldtoNew[node] = Node(node.val)
            for neighbor in node.neighbors:
                dfs(neighbor)
        dfs(node)
        def dfs(node):
            for neighbor in node.neighbors:
                OldtoNew[node].neighbors.append(OldtoNew[neighbor])
        return 
```
