---
title: "projectM Installation/Build Problems"
date: 2010-11-19
forum: General Help
---

### Post by Arythael on 2010-11-19
I'm trying to install the projectM visualizer and I'm running into some problems. Initially, I tried to install it by running "sudo apt-get install libvisual-projectm", which seemed to work... except there's no launcher for it in my Applications menu and "projectM-pulseaudio" returns "command not found". From there, I decided to try to build it myself, by following [COLOR=Blue][this guide]("http://ubuntuforums.org/showthread.php?t=749793")[/COLOR] (<- link). It went well until the "make" command, which returns the following error:

```
make[2]: *** No rule to make target `/usr/lib/libGL.so', needed by `libprojectM/libprojectM.so.2.00'.  Stop.
make[1]: *** [libprojectM/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2
```I have openGL (libgl1-mesa-dev) installed, and '/usr/lib/libGL.so' exists... so I'm not really sure what the problem is. I've also added links to a "make" log and a "make -d" log, in case there's needed information in them. Any help?

```
http://dl.dropbox.com/u/8961020/projectm_make_log.txt
http://dl.dropbox.com/u/8961020/projectm_make_debug_log.txt
```

---

### Post by tgalati4 on 2010-11-19
If this is a music visualizer, then you should be able to open any popular music player (like rhythmbox) and select it from the list.  

apt-cache search projectm

Brings up a bunch of libraries, but no application called projectm, so I assume it is just a plug-in library that you install then select in your music player.  No need to recompile unless it doesn't work properly on your system.

---

