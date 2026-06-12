---
title: "mknod at startup"
date: 2010-11-18
forum: General Help
---

### Post by bluesquall on 2010-11-18
I am running a headless 10.10 server with an nVidia card for CUDA.

I've found that the devices /dev/nvidia0 and /dev/nvidiactl are not loaded at boot by default.
[INDENT]~$ cat /proc/devices | grep nvidia
195 nvidia
~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1)
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)[/INDENT]
To be able to use the card for CUDA, I need to run:
[INDENT]~$ sudo mknod -m 666 /dev/nvidia0 c 195 0
~$ sudo mknod -m 666 /dev/nvidiactl c 195 255
[/INDENT]
I don't want to have to do this every time. I think I could probably include a script in /etc/init, but I'm not sure what to trigger it on.

I'm really most interested in why it doesn't get picked up by udev and how to do this right the Ubuntu way.

---

