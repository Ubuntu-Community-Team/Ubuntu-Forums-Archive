---
title: "Getting OpenCL with an nvidia card"
date: 2012-08-29
forum: General Help
---

### Post by problemswithopencl on 2012-08-29
Hi,

I'm a bit lost when it comes to NVIDIA and their drivers... 

I have installed the driver from ppa:ubuntu-x-swat/x-updates. The NVIDIA X Server Settings tool indicates that I am running 304.43 which is to my knowledge the newest driver. The driver is installed and running. I now want to compile & run some OpenCL programs.

I got the header files from [http://www.khronos.org/registry/cl/](http://www.khronos.org/registry/cl/) in the version 1.1. I compiled my program with g++ main.cpp -o prog -lOpenCL. I get no errors during compilation. My program looks like 

```
#define __CL_ENABLE_EXCEPTIONS
#include <CL/cl.hpp>
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<cl::Platform> platforms;
    if (platforms.empty()) {
        std::cout << "No OpenCL platform found\n";
        return -1;
    }
    
}
```If I run the program then no OpenCL platform is found. :(

What am I doing wrong? Do I need to install the cuda dev driver to even execute OpenCL programs (and not only to develop them and get debug stuff)? If so, does the dev driver replace the normal driver or is it run in parallel? Is there some way I can install the dev driver without having to rerun that nvidia binary after each kernel update? I also do not need (or even want) the CUDA stuff like nvcc. Which of the files at [http://developer.nvidia.com/cuda/cuda-downloads](http://developer.nvidia.com/cuda/cuda-downloads) do I really need?


EDIT: I feel really dumb... the reason it does not work is that my code is missing cl:: Platform::get(&platforms);  Sorry if I have bothered someone.

---

