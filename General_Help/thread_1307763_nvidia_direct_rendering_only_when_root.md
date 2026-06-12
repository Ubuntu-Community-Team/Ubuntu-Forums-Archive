---
title: "nvidia direct rendering only when root??"
date: 2009-10-31
forum: General Help
---

### Post by sdowney717 on 2009-10-31
I only get direct rendering now if i run something as root using the nvidia driver 185
google earth is zooming as root with direct rendering yes, normal user very very slow. so anyone know how to fix so user gets direct rendering?

Quote:
scott@scott-desktop:~$ glxinfo | grep direct
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
scott@scott-desktop:~$ LIBGL_DEBUG=verbose

scott@scott-desktop:~$ sudo glxinfo | grep direct
[sudo] password for scott:
direct rendering: Yes
GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,
scott@scott-desktop:~$ gksudo googleearth

---

### Post by sdowney717 on 2009-10-31
some points 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249?comments=all](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249?comments=all)

[http://ubuntuforums.org/showthread.php?t=77376](http://ubuntuforums.org/showthread.php?t=77376)

edited my group file
[http://www.linuxquestions.org/questions/linux-software-2/nvidia-permission-prblems-in-application-95198/](http://www.linuxquestions.org/questions/linux-software-2/nvidia-permission-prblems-in-application-95198/)
gksudo gedit /etc/group
changed 
video:x:44:vdr,scott
to
video:x:44:scott,vdr

and this
gksudo gedit /etc/rc.local
Add the following before "exit 0":
chmod 666 /dev/nvidia* &

either or both making it work now

---

