---
title: "Two questions regarding Karmic Server"
date: 2009-11-27
forum: General Help
---

### Post by lethalfang on 2009-11-27
I'm using a P4 laptop as my home server after its internal hard drive failed. 
Anyway, I've installed Karmic Server on it. There are two things I want to do, and don't quite know how.
1) How do I change the screen resolution from the default 640x480. I've seen posts in the past suggesting adding "vga=732" in /boot/grub/menu.lst, but the new Karmic uses a different grub and the menu.lst does not exist. How do I change the screen resolution then?
2) How can I install a desktop environment (i.e. xfce) without automatically booting into it? 

Thanks in advance.

---

### Post by bodhi.zazen on 2009-11-27
To set you resolution, see :[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

In particular, set the "#GRUB_GFXMODE=640x480" line.

You can install a window manager without starting it, disable GDM.

---

### Post by lethalfang on 2009-11-27
> **bodhi.zazen said:**
> To set you resolution, see :[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

In particular, set the "#GRUB_GFXMODE=640x480" line.

You can install a window manager without starting it, disable GDM.

I changed "#GRUB_GFXMODE=640x480" to "GRUB_GFXMODE=1440x900", but it only changed the resolution of the GRUB boot menu, not the terminal after it boots into it.

---

### Post by sisco311 on 2009-11-27
> **lethalfang said:**
> I changed "#GRUB_GFXMODE=640x480" to "GRUB_GFXMODE=1440x900", but it only changed the resolution of the GRUB boot menu, not the terminal after it boots into it.

this should do the trick:[http://ubuntuforums.org/showpost.php?p=8024427&postcount=17]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17")

And to answer your second question, you could install xfce4 (meta package) it depends on the core packages of the Xfce4 desktop environment and recommends some extra Xfce4 packages.
It doesn't depend on any display manager so you will have to start an xsession with the startx command.

If you install xubuntu-desktop, you can remove gdm or disable it by renaming /etc/init/gdm.conf to /etc/init/gdm.conf.backup.

Or by starting it on runlevel 3.
/etc/init/gdm.conf:
```
description	"GNOME Display Manager"
author		"William Jon McCann <mccann@jhu.edu>"

start on (**runlevel [3]**
          and filesystem
	  and started hal
	  and tty-device-added KERNEL=tty7
	  and (graphics-device-added or stopped udevtrigger))
stop on runlevel [01**2**6]

```

---

### Post by lethalfang on 2009-11-27
> **sisco311 said:**
> this should do the trick:[http://ubuntuforums.org/showpost.php?p=8024427&postcount=17]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17")


[/code]

I did what was on that post:

I uncommented and changed a line in /etc/default/grub to
GRUB_GFXMODE=1024x768
I also tried to change that line to "set gfxmode=1024x768"

And then I added "set gfxpayload=keep" to /etc/grub.d/00_header. 

After I ran update-grub and rebooted, the screen hangs at the grub boot menu. I can SSH into the machine, but the machine itself just hangs at the boot menu. 

Any ideas?

Thanks in advance.

---

### Post by lethalfang on 2009-11-27
Oh crap, my grub broke! I've no idea why I tried to revert all the changes I've made (i.e., taking away the extra line I added at /etc/grub.d/00_header and re-commented the line at /etc/default/grub), but then my monitor is **still** stuck at the boot loader screen, even though the countdown shows at 0 second. 
I can still SSH into my server, but I can't do anything on the machine itself.... hmm.......
Anyone knows how to restore the grub?
Thanks.

EDIT: I "fixed" the grub menu hanging problem. It's really odd. I cp'ed a backup copy of "00_header" to "old_00_header", and when I cat'ed /boot/grub/grub.cfg, it appeared to be looking for old_00_header, so I mv'ed "old_00_header" to ".00_header.old," and the grub loader was able to proceed, although I still cannot get the desired resolution in my server's terminal.
I can get the desired resolution in the grub menu, but the resolution goes back to 640x480 when it boots into the terminal.

---

