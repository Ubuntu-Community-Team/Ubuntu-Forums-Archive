---
title: "vnc server with xinet.d session access"
date: 2010-02-20
forum: General Help
---

### Post by jcvalverde on 2010-02-20
Hi,

 I set up a VNC server to autostart with my home server (yes, what a geek) by generally following the instructions from this post:

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

which I didn't think of posting back on since it's so old.

My problem: the session seams limited: I can't mount usb drives, or shutdown the computer for example.

I've looked around for help (googled actually), but all I've found is a couple of threads pointing out that since the session is started by VNC this is a SELinux feature blocking the remote user from doing "local" stuff.

I understand it's a feature, I just want to disable it since my main problem is that I don't have a monitor for my server. I used to access it through SSH but now I have a couple of servers I want to run that require a visual interface, plus now I have some data that I need to access from an external hard drive.

Regards,

---

