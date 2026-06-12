---
title: "Ubuntu boots and mounts a dummy directory"
date: 2010-10-17
forum: General Help
---

### Post by gkinal on 2010-10-17
I had a problem with Ubuntu 10 trying to mount a non-existent directory, mount/DRIVE_F/R&RMT .  It would post an error message, wait for acknowledgement (or timeout).

The only cure for this incredible annoyance was to manually create the missing directory and path.

This works, EXCEPT THAT now instead of the (Gnome) desktop coming up, the empty directory I created comes up, and I have to close or minimize it.

I can't find where in the boot process the command to mount this occurs.

I need a clear explanation of the complete boot process from cold boot to Gnome GUI exposition.

G.

---

### Post by Barriehie on 2010-10-17
If you run ```
$ >dmesg
``` right after boot it will show you boot steps.

HTH

---

### Post by yetiman64 on 2010-10-18
Use ```
cat /etc/fstab
``` to check your fstab file for the problematic path.

If it exists in fstab then you will need to comment out (#) the line containing it. If you wish, you can post the output of that command here for perusal before any editting.

If the path exists in fstab. To edit fstab,
```
gksudo gedit /etc/fstab
``` and place your cursor at the start of the line it is in and insert a # symbol. Save and close the file and then use,

```
sudo mount -a
``` post any errors outputted by this command or if no errors then all should be OK.

---

### Post by dcstar on 2010-10-18
> **gkinal said:**
> I had a problem with Ubuntu 10 trying to mount a non-existent directory, mount/DRIVE_F/R&RMT .  It would post an error message, wait for acknowledgement (or timeout).
............

And did you have some external device plugged in when you installed Ubuntu that is no longer there?

---

