---
title: "Can't boot, Regular OR Recovery Mode (Meerkat)"
date: 2011-01-01
forum: General Help
---

### Post by el canadiano on 2011-01-01
Hey guys,

I have GRUB on my laptop with Ubuntu and Windows 7. GRUB and Windows 7 seem to boot just fine, but recently, Ubuntu doesn't boot.

My suspected cause is simply because I've often shut down unofficially. My laptop doesn't have a battery, and even the AC connection is awry, so as soon as an accidental disconnection or something occurs (because it too is broken), it'll essentially shut down.

I try booting Ubuntu, and it doesn't boot. I think I see that Ubuntu and the dots page, but it'll hang there (and I waited overnight). Immediately, I want to run an fsck, but I seem to be unable to, so I run Recovery Mode. I always get a forever loop of a bunch of stuff that doesn't make sense to me, but this is one thing that I always see (or something similar).

> [295.439361] EXT4-fs error (device sda5): __ext4_get_inode_loc: inode #1571 (comm pci-db) unable to read inode block 525047

Here are also two screenshots. Let me know if something else might help solve my problem.

---

### Post by drs305 on 2011-01-01
If you can boot a LiveCD, you can start up Disk Utility (System, Administration). Highlight the Ubuntu partition and in the lower panel you can run "Check Filesystem". You can perform a similar check from Gparted.

---

### Post by el canadiano on 2011-01-01
According to it, it says "File System is Clean." After trying to reboot in Recovery Mode, it didn't seem like it fixed anything.

---

### Post by el canadiano on 2011-01-02
Ignore my last post, I did it wrong. After checking the filesystem of my ext4, my file system is **not** clean, but how does it get fixed?

---

### Post by drs305 on 2011-01-02
> **el canadiano said:**
> Ignore my last post, I did it wrong. After checking the filesystem of my ext4, my file system is **not** clean, but how does it get fixed?

From the LiveCD, you can run the repair via System, Administration, Gparted. Make sure the partition is NOT mounted, then highlight it and select "Partition, Check". It will run this command automatically:
```
e2fsck -f -y -v /dev/sdXY
```

---

### Post by el canadiano on 2011-01-03
> **drs305 said:**
> From the LiveCD, you can run the repair via System, Administration, Gparted. Make sure the partition is NOT mounted, then highlight it and select "Partition, Check". It will run this command automatically:
```
e2fsck -f -y -v /dev/sdXY
```

Thanks for that.

So I ran fsck, but I couldn't do graphical boot. The bad sectors on the partition seemed to screw over a few of the things to do that, so how do I go about now to repair boot and all that?

---

### Post by drs305 on 2011-01-03
> **el canadiano said:**
> Thanks for that.

So I ran fsck, but I couldn't do graphical boot. The bad sectors on the partition seemed to screw over a few of the things to do that, so how do I go about now to repair boot and all that?

Are you still getting error messages regarding the filesystem from the original post? Is the boot process getting past Grub2 and passing control over to the kernel (i.e. failing later in the boot)?

If it is failing later in the boot you probably have a problem not involving grub. There have been posts in the past several days about updates breaking video. You may need to boot by adding the 'nomodeset' option to the end of the 'linux' line during boot and then adding your video driver via "System, Administration, Additional Drivers".

But I may be getting ahead of your situation. If you see the menuentry, you might edit it (press "e") and remove "quiet splash", then CTRL-x to boot. See if there are any errors as it boots. (If you don't see the menu at boot, try holding down the SHIFT key during boot until it appears.)

---

### Post by el canadiano on 2011-01-03
> **drs305 said:**
> Are you still getting error messages regarding the filesystem from the original post? Is the boot process getting past Grub2 and passing control over to the kernel (i.e. failing later in the boot)?

If it is failing later in the boot you probably have a problem not involving grub. There have been posts in the past several days about updates breaking video. You may need to boot by adding the 'nomodeset' option to the end of the 'linux' line during boot and then adding your video driver via "System, Administration, Additional Drivers".

But I may be getting ahead of your situation. If you see the menuentry, you might edit it (press "e") and remove "quiet splash", then CTRL-x to boot. See if there are any errors as it boots. (If you don't see the menu at boot, try holding down the SHIFT key during boot until it appears.)

Grub isn't the problem, and it doesn't seem like it ever was the problem. I'm pretty sure now it was just my ext4 /dev/sda5 drive that had Ubuntu had some bad sectors or something. Thus, your first paragraph is all yes. I saw an error saying that I had to repair something which I think is critical to a graphic boot (like the ordinary stuff), but I don't know how to get around that. But my problems didn't come from an update, I'm pretty sure it came from not shutting down properly, as I said why previously.

---

### Post by el canadiano on 2011-01-10
I pulled this off from some of the lines of "warning."

WARNING: unable to load file '/etc/gdm/custom.conf': No such file or directory

I look up and see that I can somehow type in sudo gdmsetup. What does that do and will it help? Oh, and I still can't get into Terminal.

---

