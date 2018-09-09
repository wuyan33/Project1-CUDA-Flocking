**University of Pennsylvania, CIS 565: GPU Programming and Architecture,
Project 1 - Flocking**

* Yan Wu
  * [LinkedIn](https://www.linkedin.com/in/yan-wu-a71270159/)
* Tested on: Windows 10, i7-8750H @ 2.20GHz 16.0GB, GTX 1060 6GB (Personal Laptop)
* [Repo Link](https://github.com/wuyan33/Project1-CUDA-Flocking)
### Program Result:
* Result GIFs on 5,000 boids:
  * Naive (by LICEcap):<br />
    <img src="/images/naive.gif" width="80%">
  * Uniform grid (by ScreenToGif):<br />
    <img src="/images/uniformGrid.gif" width="80%">
  * Coherent Search (by ScreenToGif):<br />
    <img src="/images/coherentSearch.gif" width="80%">
### Performance Analysis
  * Framerate change with increasing # of boids for naive, scattered uniform grid, and coherent uniform grid (with visualization): <br />
    <img src="/images/visualized_boids.PNG" width="80%"><br />
  * Framerate change with increasing # of boids for naive, scattered uniform grid, and coherent uniform grid (without visualization): <br />
    <img src="/images/nonvisualized_boids.PNG" width="80%"><br />
  We can see that with the increasing number of boids, FPS of all three methods are decreasing. Clearly naive method performs worst with higher boid number.
  * Framerate change with increasing block size: 
    <img src="/images/increaseblocksize.PNG" width="80%"><br />
  This part is tested with visualization and a boid number of 10,000.
### Q & As
* For each implementation, how does changing the number of boids affect performance? Why do you think this is?
  * For the naive method, increasing number of boids let to significantly decreasement in FPS, that's because brute force is an algorithm with a time complexity of O(N^2). The other two methods decrease as well but in a lot lower rate. That's because both algorithms have almost linear time complexity.
* For each implementation, how does changing the block count and block size affect performance? Why do you think this is?
  * From my result where I chose block count from 32 to 512, changing block count doesn't seem to have significant impact on performance. 
* For the coherent uniform grid: did you experience any performance improvements with the more coherent uniform grid? Was this the outcome you expected? Why or why not?
  * Not so much. I expected coherent method to win, but turns out the two algorithms has about the same performance. I tested for several times, but the performance are different from each others. There were two times FPS for uniform grid method has a difference of over 100. Unsteady outcome might be one of the reasons.
* Did changing cell width and checking 27 vs 8 neighboring cells affect performance? Why or why not? Be careful: it is insufficient (and possibly incorrect) to say that 27-cell is slower simply because there are more cells to check!
  * In my case, performance with 27 neighboring cell is almost the same as 8 neighboring cell when boid number is below 10000. Then as boid number increases, my result has a preference for 8 neighboring cell. While checking 27 neighbors did requires more time to each thread, the cell number decreases as cell become larger. 
