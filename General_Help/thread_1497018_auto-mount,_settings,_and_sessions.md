---
title: "auto-mount, settings, and sessions"
date: 2010-05-30
forum: General Help
---

### Post by Ron O on 2010-05-30
How do I get an auxiliary drive to mount on each boot? All my music files are on a separate hard drive which I have had to manually mount then repopulate the library in Rhythmbox each time I reboot.

Along the same lines, how do I get Ubuntu to remember settings in various applications without saving an entire session? For example, the screen capture utility always starts with "capture entire screen" and I have to keep selecting select part of screen to capture.

If I must do this by saving the session, how do I do this? I can't find anything on the menus.

---

### Post by garvinrick4 on 2010-05-30
> **Ron O said:**
> How do I get an auxiliary drive to mount on each boot? All my music files are on a separate hard drive which I have had to manually mount then repopulate the library in Rhythmbox each time I reboot.

Along the same lines, how do I get Ubuntu to remember settings in various applications without saving an entire session? For example, the screen capture utility always starts with "capture entire screen" and I have to keep selecting select part of screen to capture.

If I must do this by saving the session, how do I do this? I can't find anything on the menus.Is this a USB drive?

---

### Post by Ron O on 2010-05-30
No, it is actually just a separate partition on my Ubuntu drive. It shows up on the Ubuntu Places menu, but is unmounted until selected for mounting. I should have been a little more clear about that.

---

### Post by garvinrick4 on 2010-05-30
> **Ron O said:**
> No, it is actually just a separate partition on my Ubuntu drive. It shows up on the Ubuntu Places menu, but is unmounted until selected for mounting. I should have been a little more clear about that. I am sorry I have never tried to auto-mount internal drive partitions, just USB externals. But it is worth googling around to see if there is a way to get a seperate /home or data partition to mount at boot. I will let you know if I find a viable solution. If is anywhere will be in configuration editor.
   You know there is a panel add called "disk mounter" that gives you a applet to mount or unmount your partitions internal or USB on upper or lower panel. Saves one movement. 
Right click on upper or lower panel and Add to Panel..

---

### Post by garvinrick4 on 2010-05-30
> **Ron O said:**
> No, it is actually just a separate partition on my Ubuntu drive. It shows up on the Ubuntu Places menu, but is unmounted until selected for mounting. I should have been a little more clear about that.
Here is a line of code I have not tried but the link is the superusers.com one below. Please post on this thread
the results so I can put in my cheat sheet of code. I have myself no desire to mount any partitions on boot but
I saw a lot of people who did during research.

```
gnome-mount -p Data(change it to your volume label)
``` Now drive will be mounted at startup and 
you will be able to mount/unmount it without any errors.

[http://superuser.com/questions/62483/automount-in-ubuntu-9-10](http://superuser.com/questions/62483/automount-in-ubuntu-9-10)

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

