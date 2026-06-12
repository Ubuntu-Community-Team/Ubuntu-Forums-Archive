---
title: "Disappearing Icons"
date: 2009-08-05
forum: General Help
---

### Post by epic concept on 2009-08-05
For some odd reason the Hard drive icons on my desktop disappear when I reboot the machine, I have to click on Places > Hard drive to get them back on the desktop.

How do I get them to stay there?

---

### Post by credobyte on 2009-08-05
Have you added it to fstab ( [http://www.stchman.com/part.html](http://www.stchman.com/part.html) ) ?

---

### Post by epic concept on 2009-08-05
What am I doing with that, I have no Idea!

---

### Post by scouser73 on 2009-08-05
Enter this code into terminal.

> gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible true

---

### Post by CatKiller on 2009-08-05
> **epic concept said:**
> What am I doing with that, I have no Idea!

fstab (the filesystem table) contains a list of partitions that you want mounted (ie, accessible) when you boot the computer. If you mount them to somewhere in /media (which is the default when you double-click to access them) then you'll get icons on the desktop. If you mount them somewhere else, you won't.

We can help you with the entries, but we'd need to know what you've got already. The outputs of 

```
fdisk -l
``` and ```
cat /etc/fstab
```would be a useful start.

---

### Post by epic concept on 2009-08-05
When I do the **gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible true** 			 		  command it says

**bash: gcpmftool-2: command not found**.


I did the fstab

Here's what I get
 
[B]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=32569e03-3dc7-4c1b-9b41-4300afab4b0a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=3bb593dd-a915-4061-bbf6-50277faab500 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/B]


Sorry I have no Idea how to put that in a quote box.

---

### Post by CatKiller on 2009-08-05
> **epic concept said:**
> When I do the **gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible true**                        command it says

**bash: gcpmftool-2: command not found**.

You've got a typo there.

It won't help you, anyway. That's to set the display of mounted devices on the desktop, which you've already got. What you want is to mount your devices automatically.

> I did the fstab

We'll need the fdisk output, too, to actually know which partitions that you've got that you want entries for.

> Sorry I have no Idea how to put that in a quote box.

Wrapping it in either [CODE] tags or [QUOTE] tags will do it. (Code tags are often better, since the box will be scrollable if the contents are long, which makes reading the rest of your message easier)

---

### Post by epic concept on 2009-08-05
Another Problem  I installed cairo dock but when I try to launch it from the Terminal using cairo-dock it gives the following error warning :  (cairo-dock.c:main:414)    couldn't create directory /home/christian/.config/cairo-dock  How do I fix that?  BTW I don't have compiz installed I'm running Gnome if that matters.

---

### Post by CatKiller on 2009-08-05
> **epic concept said:**
> Another Problem

Best start a new thread on that one. Then someone who's used Cairo Dock might be able to help you.

---

