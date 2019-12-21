# Number-of-Islands
Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

https://leetcode.com/problems/number-of-islands/

Example 1:
```
Input:
11110
11010
11000
00000

Output: 1
```

Example 2:
```
Input:
11000
11000
00100
00011

Output: 3
```

Solution:
```
class Solution {
    
    class Position {
        public int x;
        public int y;
        public Position(int x, int y){
            this.x=x;
            this.y=y;
        }
    }
    
    public int numIslands(char[][] grid) {
        HashSet<Position> visited = new HashSet<>();
        int numIslands = 0;
        for(int x = 0; x < grid.length; x++){
            for(int y = 0; y < grid[x].length; y++){
                Position current = new Position(x,y);
                if(grid[x][y] == '1' && !visited.contains(current)) {
                    numIslands++;
                    markIslandVisited(x, y, grid);
                }
            }
        }
        return numIslands;
    }
    
    void markIslandVisited(int x, int y, char[][] grid) {
        if(0 <= x && x < grid.length &&
           0 <= y && y < grid[x].length &&
               grid[x][y] == '1') {
            grid[x][y] = '0';
            markIslandVisited(x+1, y, grid);
            markIslandVisited(x-1, y, grid);
            markIslandVisited(x, y+1, grid);
            markIslandVisited(x, y-1, grid);
        }
        return;
    }
}
```
