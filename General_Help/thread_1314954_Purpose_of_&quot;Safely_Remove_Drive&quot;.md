---
title: "Purpose of &quot;Safely Remove Drive&quot;"
date: 2009-11-04
forum: General Help
---

### Post by Ashfire908 on 2009-11-04
In 9.04, there was unmount and eject, which, obviously, unmount unmounted the device/drive/partition/whatever, and eject put a drive into a state where it was ready to be removed. Now, in 9.10, there's a new option: Safely Remove Drive. Obviously, this was worded for the Windows users, because it's the most familiar option (as unmount is totally foregin and eject is close but not the 'obvious' option). It appears just to copy the Windows XP function (which for the life of me I don't know why XP cuts power to the device when ejecting, as Vista droped the cut the power part), but I'm wondering, does it actually serve a purpose beyond reducing people asking how you remove a device? And if it doesn't, how can I remove the option form the menu? (It's a bit cluttered with the other two options.)

---

### Post by soni1770 on 2009-11-05
i think safely remove drive powers down the drive head, so that when the power is cut it doesn't hang over the disk, 
maybe

---

### Post by 3rdalbum on 2009-11-05
> **soni1770 said:**
> i think safely remove drive powers down the drive head, so that when the power is cut it doesn't hang over the disk, 
maybe

Linux does this anyway when unmounting, and I think I remember hearing that a lot of drives can do it automatically when they get powered-down. Also, the "safely remove" option is provided on flash drives.

---

### Post by alphaniner on 2009-11-05
I've heard it suggested that it is directed at Windows users.  For those not aware, 'Safely Remove' is the Windows way of unmounting removable media like flash drives.

---

### Post by Ashfire908 on 2009-11-05
> **3rdalbum said:**
> Linux does this anyway when unmounting, and I think I remember hearing that a lot of drives can do it automatically when they get powered-down. Also, the "safely remove" option is provided on flash drives.

Yes, when a hard drive loses power, the drive automatically parks the heads (on it's own, without being told to).

Linux does not power off the device when unmounting, nor does it when ejecting.

---

### Post by ubfu on 2010-01-31
I wanted to know command to triggered "Safely Remove Drive".So I could implement it on Hardy 8.04

---

### Post by tehweezil on 2010-03-11
I dunno, but I accidentally hit "Safely Remove Drive" instead of "Unmount" a few minutes ago and then the majority of my removable drives disappeared and/or unmounted and now I can't get them to remount, even after logging out and back in :'( Imma try to just restart it though.

The "Unmount" option is pretty convenient though :P

---

### Post by stoneage on 2010-03-11
> **tehweezil said:**
> I dunno, but I accidentally hit "Safely Remove Drive" instead of "Unmount" a few minutes ago and then the majority of my removable drives disappeared and/or unmounted and now I can't get them to remount, even after logging out and back in :'( Imma try to just restart it though.

The "Unmount" option is pretty convenient though :P
If you Safely removed them, they have no power. Try removing and replugging, should do it.....

Safely remove, does, as far as I can tell, power off and unmount. Unmount just unmounts. Useful if you want to reformat.

---

### Post by tehweezil on 2010-03-11
> **stoneage said:**
> If you Safely removed them, they have no power. Try removing and replugging, should do it.....

Safely remove, does, as far as I can tell, power off and unmount. Unmount just unmounts. Useful if you want to reformat.

Yeah I did that before I logged off and the devices didn't remount. The restart did the trick though, so yeah if anyone else has that problem a successful restart should help.

---

### Post by nemilar on 2010-03-12
One of the purposes of the safe-remove feature (and I believe this applies to Windows as well as Linux) is to force the OS to flush the contents of the write cache to disk (whether it be hard disk, flash drive, or what-have-you).

When you write to a disk device, your writes aren't always directly written to the physical medium.  Linux will buffer the writes in RAM first.  If you yank the drive from the USB port before the OS has flushed the cache contents to the drive, you will effectively lose this data.

You can try it yourself.  Plug in a device, mount it, and copy a very large file to it.  You can watch the write cache fill up:

```
watch -d -n 1 "cat /proc/meminfo | grep Dirty"
```

And you can manually force a flush of this data to disk by using this command:

```
sync
```

I don't know if this is the *only* reason for the safe-remove, but I do believe it is one of the primary reasons.  So yes; you should use it.

---

