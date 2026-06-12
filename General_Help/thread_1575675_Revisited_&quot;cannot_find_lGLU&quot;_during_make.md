---
title: "Revisited: &quot;cannot find lGLU&quot; during make"
date: 2010-09-16
forum: General Help
---

### Post by ladasky on 2010-09-16
Hi!

I just encountered a problem _[similar to this one]("http://ubuntuforums.org/showthread.php?t=1441029")_, posted a few months ago.  Unfortunately the solution posted is NOT working for me.  ](*,)  I think I can see why, the original poster apparently had a corrupted gtkglarea package.  I'm not trying to install gtkglarea.
 
If you care, what I am trying to do is install CUDA on Karmic.  I have successfully installed a recent NVidia driver (devdriver_3.1_linux_32_256.40.run), which is the one specified for use with the CUDA 3.1 core package (cudatoolkit_3.1_linux_32_ubuntu9.10.run).  To confirm that everything is working, NVidia provides working examples of CUDA code, shipped as source (gpucomputingsdk_3.1_linux.run).  I'm trying to compile that source, and that's where I get stuck.
 
NVidia's instructions tell you to go into a certain directory and execute a make.  Make runs for a while, and spits out several warnings, but finally stops.  Here are the last few lines of the log:
 
```
nvopencc WARNING: -noinline or -INLINE:=off has been seen, -default_options ignored
/usr/bin/ld: cannot find -lGLU
collect2: ld returned 1 exit status
make[1]: *** [../../bin/linux/release/FunctionPointers] Error 1
make[1]: Leaving directory `/home/john/NVIDIA_GPU_Computing_SDK/C/src/FunctionPointers'
make: *** [src/FunctionPointers/Makefile.ph_build] Error 2

```

 
_[This web page]("http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux/Missing_-lGLU_compile_error")_ suggests that the problem might be that the CUDA examples want to use a part of OpenGL.  In the example, OpenGL IS already installed on the computer (as I believe it is on mine), but the file "libGLU.so" needs to have a link to it placed in /usr/lib.
 
I'm a little confused by the fact that the error message says "cannot find lGLU" instead of "cannot find libGLU".  :???:   Also, I don't have a directory named /usr/X11R6, or anything close to that.  Finally, searching through my whole file system, I don't see a file named "libGLU.so" anywhere.  I did, however, locate two files whose names are quite close to that:  "libGLU.so.1.3.070600" and "libGLU.so.3.8.0", both in /usr/lib.  They are accompanied by two suggestively-named links,  "libGLU.so.1" and "libGLUT.so.3".  Presumably the first link points to the first file, and the second link to the second file.

So, is the problem that Linux repositories have started adding revision numbers to the "libGLU" file name that was once generic?  In that case, should I just create a link to one of the libGLU.so files that I have?  If so, to which file should I link? 
 
Alternately, am I looking for some other "libGLU" file entirely?  If so, where do I find it?  Searching for "libGLU" in the package manager comes up with eleven packages.  I do have libglu1-mesa installed, but none of the others.
 
NVidia has a forum for CUDA users/developers, but it's VERY quiet.  More than one person has posted questions very similar to mine, and I can see that they have gone unanswered for several days.  I hope to have better luck here, you folks have never let me down!  :D

---

### Post by ladasky on 2010-09-16
Well, I solved my own problem, though with less than complete understanding of what I was doing.
 
More searching turned up _[this post]("http://forums.nvidia.com/index.php?showtopic=164853")_ at NVidia forums.  To build the CUDA examples on Karmic, you need the following packages: libglu1-mesa-dev, libxmu-dev, and freeglut3-dev.  This is not in NVidia's documentation (which I guess makes sense, as they can't know what your personal Linux may include).
 
All the error messages disappear, but there are a ton of warnings during the build.

I'm still not quite sure how to get from the name of a file that's missing to the package that contains it.  Missing-file/package error messages are more descriptive when you install a Python application -- the names actually match!

---

