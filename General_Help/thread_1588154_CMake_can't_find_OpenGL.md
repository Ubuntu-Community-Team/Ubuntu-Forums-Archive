---
title: "CMake can't find OpenGL"
date: 2010-10-04
forum: General Help
---

### Post by acidblue on 2010-10-04
I'm trying to install Kicad from source but cmake gives me an error:
"- Check for installed OpenGL -- not found
CMake Error at CMakeModules/CheckFindPackageResult.cmake:6 (message):
  OpenGL was not found - it is required to build Kicad  "

I have an Nvidia video card with the proprietary drivers installed.
I also have glut, (glutg3) installed.
I don't understand why cmake can't find OpenGL.

Can someone shed some light on this.

Ubuntu 10.04 64 bit.

---

### Post by andrewthomas on 2010-10-04
Post the output of

```
glxinfo|grep OpenGL
```

---

### Post by acidblue on 2010-10-04
Here it is:
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.36.24
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler
OpenGL extensions:

---

### Post by andrewthomas on 2010-10-04
What's wrong with the version in the repos?

[http://packages.ubuntu.com/search?keywords=kicad](http://packages.ubuntu.com/search?keywords=kicad)

---

### Post by acidblue on 2010-10-04
It's too old.

---

### Post by andrewthomas on 2010-10-04
Do you have the build dependenceis?

```
sudo apt-get install build-essential checkinstall
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by acidblue on 2010-10-04
Yes I do.

---

### Post by andrewthomas on 2010-10-04
Have you tried this ppa?

[https://launchpad.net/~paxer/+archive/ppa]("https://launchpad.net/%7Epaxer/+archive/ppa")

or alternatively 
> 
If you get the error message that the opengl library could not be found,  look in your /usr/lib directory. CMake searches for the libGL.so file.  If only  libGL.so.1 is present create a symbolic link: 'sudo ln -s libGL.so.1  libGL.so'. 

[https://answers.launchpad.net/kicad/+faq/1050](https://answers.launchpad.net/kicad/+faq/1050)

---

### Post by acidblue on 2010-10-04
It seems I don't have a libGL.so file just a libGLU.so.1 file.

As for Launchpad, I'm having problems with that as well.
Check my post on Kicad:
[http://ubuntuforums.org/showthread.php?t=1586972](http://ubuntuforums.org/showthread.php?t=1586972)

---

### Post by Ayuthia on 2010-10-04
Have you tried:
```

sudo apt-get build-dep kicad

```
To see if you have all the dependencies for the package?

---

### Post by acidblue on 2010-10-04
No I didn't , but I did just know and Cmake now works fine.
Thanks:)

---

### Post by andrewthomas on 2010-10-04
Glad to be of help.

---

