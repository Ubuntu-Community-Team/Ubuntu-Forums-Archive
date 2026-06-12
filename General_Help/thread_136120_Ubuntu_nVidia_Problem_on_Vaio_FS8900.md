---
title: "Ubuntu nVidia Problem on Vaio FS8900"
date: 2006-02-25
forum: General Help
---

### Post by evadave on 2006-02-25
I have a new Sony Vaio FS8900 laptop - I am so far very very impressed with how Ubuntu has supported everything. Sound, wireless, network, etc. It all works well. I've had a slight problem with tty's and shutdown, but nothing I care about right now and will probably be fixed by playing about with acpi.

The problem I am having is with the nVidia graphics card (GeForce 6400 Go TurboCache 128). This is strange given thats the one thing I had counted on working totally and have thus far never had a problem with on other systems.

My method was to apt-get install nvidia-glx (the kernel modules and the nvidia-kernel-common where of course pre-installled). I then simply ran nvidia-glx-config enable.

GLX appears to start fine (according to the log), glxinfo suggests that direct rendering is on and working fine, and nvidia-settings suggests everything is fine too. However, despite that, and despite ldd showing that glxgears is linking to the nvidia OpenGL libraries glxgears and any 3D acceleration simply doesn't work. DVD's are jumpy and slow, as if the graphics is just not accelerated, glxgears runs very very slow.

I'm basically stumped and I'd appreciate any help you may have or pointers to those places or people who could help me. Hopefully I can get this last peice of the puzzle solved and I won't have to use Windows.

Thanks in advance

---

