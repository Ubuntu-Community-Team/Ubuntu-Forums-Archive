---
title: "Something wrong with my xserver driver (i think)"
date: 2009-11-02
forum: General Help
---

### Post by adrian.h on 2009-11-02
I think the problem is my driver as I was trying to get better performance from my video card by getting another driver. But instead, it really messed up my local login to the point that I cannot even use the keyboard to switch to another console. I can login to the Ubuntu box via xdmcp session and ssh, so the Xserver is working as is terminal services. The video was showing nothing, but now is showing the startup graphic when Ubuntu shows on startup, except it is not at the same resolution as I'm seeing two of them side by side and in very strange colours.

I've tried to use the command:
[INDENT]   sudo dpkg-reconfigure xserver-xorg
[/INDENT] But it doesn't ask for a video type, which is what I was expecting.

Is there anyway of resetting the video settings somehow to get it to where it was when I installed Ubuntu at the beginning? It was a little slow, but at least it had 3D capabilities and I could use it locally.

The system is a INTEL P4 with 1GB RAM running Juanty 9.04 Ubuntu. If you need more info, please tell me how to get that info and I will provide it.

Thanks for your help.

---

