---
title: "Repair grub after GParted LIVE CD Copy?"
date: 2011-05-03
forum: General Help
---

### Post by windyweather on 2011-05-03
I posted this over at GParted Forum, but they may be asleep and I want to get my system going again.

I'm upgrading a disk on an Ubuntu 10.04 system.
Used Gparted Live CD and all went well, but of course it won't boot now.

So. I have GLiveCD booted now, and am trying to do instructions here:
[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem)

Glad to see that grub is on the GParted LiveCD.

But the commands give an error. For both Find commands I get Error 15: File Not Found. hmm
Which probably means that I need to mount the /dev/sda1 file system - which is the ext4 file system that I copied - GParted says that went successfully.

mount /dev/sda1 does not work - something about the partition not in the fstab - which of course it wouldn't be in the GPartedLiveCD.

[ How about someday we add a "Mount" button in the GParted app, but that doesn't solve my problem now. ]

I tried the grub command:
root (hd0,0)
blind and that didn't work either. :(

So...
Can I use Grub on the GPartedLiveCD to fix up my grub to boot my disk?
What is the command sequence to fix the disk so it will boot?

gparted live CD looks like a great program. Just need this final step to get going again with my new disk. :P

Sure would be nice to repair grub from inside the gparted LiveCD, but failing that, can we figure a way to reboot the original disk and then repairing the other volume?
Or boot the Ubuntu Live CD and using that to repair grub.

Thanks a heap,

-WW

---

### Post by drs305 on 2011-05-03
[s]I can guarantee it, but I'm not sure Grub legacy can use ext4.[/s] *Thanks TeoBigusGeekus*.  Additionally, 10.04 would normally use Grub2. It might be best if you downloaded the boot info script from the following link. From a LiveCD, run the script, then post the contents of RESULTS.txt

It will show us the status of your boot files.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

And just to be clear, when you say 'boot your disk' are you trying to just boot a normal Ubuntu installation or are you attempting to do something else?

---

### Post by oldfred on 2011-05-03
the instructions you are following are for grub legacy (0.97). Ubuntu is now using grub2. Ubuntu 11.04 is grub2 (1.99) and I think your 10.04 was 1.97.

You need a liveCD of 10.04 and use the grub2 repair commands. Error 15 is from grub legacy and is usually a conflict between grub & grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by TeoBigusGeekus on 2011-05-03
> **drs305 said:**
> I can guarantee it, but I'm not sure Grub legacy can use ext4.

It can; I use grub legacy and all my partitions are ext4.

---

### Post by wilee-nilee on 2011-05-03
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

You will use a live cd to fix this unless we can get into the OS. It sounds like you moved the front of the partition that is the /boot.

This script will get us down to bidness.;)

---

### Post by windyweather on 2011-05-03
Wow. Thanks.Yep. I'll be back in a few with the results.

- ww

---

### Post by wilee-nilee on 2011-05-03
> **windyweather said:**
> Wow. Thanks.Yep. I'll be back in a few with the results.

- ww

Hey used to live in Myrtle Creek.

---

### Post by windyweather on 2011-05-03
Only been here in Or for six years. Love coastal living, and the quiet small town.

Here are the results.
Thanks,
ww
:guitar:

---

### Post by drs305 on 2011-05-03
Grub 2 isn't installed in an MBR, so you should install it to your Ubuntu drive (sda). Boot the LiveCD, then in a terminal mount your Ubuntu partition and run these commands to mount your Ubuntu partition and point the MBR to sda1:```


sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot. Don't put the partition number in the second command.

---

### Post by windyweather on 2011-05-03
That did it.
Thanks.
ww

---

