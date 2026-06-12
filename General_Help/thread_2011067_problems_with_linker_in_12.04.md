---
title: "problems with linker in 12.04"
date: 2012-06-26
forum: General Help
---

### Post by exedor on 2012-06-26
Hi all,

First, thank you for reading this :)

Before you tell me I need to go ask this question in a gcc or development related forum, I'm asking it here because I'm hoping someone who understands how gcc/g++ etc.. was packaged for Ubuntu will understand/respond/redirect.

I have a large complex application, call it bob, historically maintained on Fedora.  Granted I'm running Ubuntu server (to keep it stripped down) and then adding the packages I need to build the software (make, cmake, gcc, g++, dev libraries from various other software packages, OpenThreads, OpenSceneGraph, boost, etc...)

Everything compiles, links, and runs fine under Fedora.  Under Ubuntu I've worked through all the issues except this very strange and what I consider bizarre problem:

The build system in the application "bob" does this:

1: Compiles a set of .o files in a rendering library called libRender.a
2: Archives them using ar into a .a library
3: Compiles the rest of the libraries with their respective .cpp files into .o and later .a lib files
4: Compiles subsystems into .so shared libraries during which the .a files are linked to and referenced.
e.g.:
g++  -g -gstabs+ -DOSG_COMPILE_UNIT_TESTS   -L/usr/X11R6/lib64 -L../../../../local/lib  -L../../../../devel/lib/Linux64  -shared  DAHud.o DynamicManager.o  EnvironmentManager.o HudManager.o StaticManager.o TileGroup.o ViewMode.o Visuals.o VisUtils.o CameraPlatform.o ViewModeFirstPerson.o ViewModeThirdPerson.o  VisData.o Visuals.o -losgGA -losgViewer -losg -losgUtil  -losgDB -losgParticle -losgText -losgSim -losgFX -lOpenThreads -lsApp  -lRender -ljpeg -lxclApp -lboost_signals -o Visuals.so

From this you can see the series of osg (OpenSceneGraph) libraries being linked.  Both OpenThreads and OpenSceneGraph are not built from source but using Ubuntu packages instead.

All of this compiles just fine but when you go to run it, an error is thrown about unresolved symbols.  Running ldd on Visuals.so clearly shows that osgSim, the library containing the definition for the symbols on question was omitted as a dependence from the generated Visuals.so file, while others such as osgUtil were not.  Now here is the problem.

It appears that any of the libraries required directly by .o files in the g++ command above linking Visuals.so are included and named as a dependency but any libraries required by any of the .o files in libRender.a are omitted and ignored causing fatal runtime issues.

I've seen similar behavior when trying to build a simple utility called G25manage used for kicking the logitech G25 and G27 wheels into native mode from backward compatibility mode.  It requires libusb.  I installed all the libusb and development packages along with their shared libraries, and no matter what I do I cannot get it to compile using the shared libraries even though they are in the search path.  I had to link against the static library for libusb to make that work.

Before you start taking issue with 64-bit versus 32-bit let me say I've setup both the 32 and 64 bit versions in Virtual Machines and get identical results.

Why is this an issue on Ubuntu?  I suppose it could be related to different compiler versions, I haven't yet checked which version of the compiler I'm running on Fedora but it is whatever ships with Fedora Core 13 (probably older than what comes with Ubuntu.)

Sorry for the long post.  Thanks for looking!
Ex

---

### Post by dino99 on 2012-06-26
i've no experience on that, but this could help you know about ubuntu side packaging

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

