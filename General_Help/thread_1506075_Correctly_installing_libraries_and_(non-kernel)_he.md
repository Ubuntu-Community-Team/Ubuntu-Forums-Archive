---
title: "Correctly installing libraries and (non-kernel) header files"
date: 2010-06-09
forum: General Help
---

### Post by mark.diamond on 2010-06-09
Not sure which forum to post this in ... a question about libraries and header files.

I recently installed a package (Vision Egg) that requires the Open GL libraries and headers, specifically, gl.lib and gl.h.  I used Synaptic to install nvidia-current and nvidia-current-dev and it now looks as if the required libraries (under different names) are installed in /usr/lib/nvidia-current and as if the required headers are in /usr/include/nvidia-current. I am a bit confused because I also have /usr/lib/nvidia and /usr/lib/nvidia-173.

The installation of Vision Egg fails with "cannot find GL/gl.h" and "/usr/bin/ld: cannot find -lGL"

There is a related post a few years ago under thread 200901 but it relates only to a single file problem that is fixed manually. I'd rather avoid that because it looks like it is easily breakable.

 Is there a *standard* way --- that is, a method that does not require error-prone manually changing or linking a multitude of file names --- of ensuring that programs which require GL/gl.h actually find the correct nvidia header file and also that the link loader finds the GL libraries.

---

### Post by jocko on 2010-06-10
You probably want the package "mesa-common-dev". Not sure you really have to use the nvidia libraries...

---

### Post by mark.diamond on 2010-06-10
> **jocko said:**
> You probably want the package "mesa-common-dev". Not sure you really have to use the nvidia libraries...

mesa-common-dev is installed. I probably don't have to use the nvidia libary but by using it, Vision Egg can make maximal use of the card capabilities (apparently).

The real issue, however, is ... "If I install something like the nvidia libraries and header files, is there a standard way (e.g., something I should be running) that will ensure that when the linker wants the GL library, it actually finds /usr/lib/nvidia-current/libGL.so or whatever?

---

