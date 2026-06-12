---
title: "Black screen when starting installer for Ubuntu Server 10.04 - XEN VNC remote"
date: 2010-05-02
forum: General Help
---

### Post by shinji257 on 2010-05-02
I have an account over at digitalswift.net.  They use Xen to do virtualization of their VPS systems.  During an OS install I can use a VNC server to get a console terminal screen.  Right after I start the install the screen just goes black.  During a fair amount of research I found that the framebuffer is being initialized for the installer on Ubuntu Server 10.04.  Is there a need to load the framebuffer to install a server distribution?

I did find a workaround.  At the menu press F6 then ESC so you have an editable command string.  Append to the end of it fb=false and then press enter.  It will load the installer fine and you should be able to finish fine.  I did not check to see if you had to add it to the grub.lst file later on.

---

