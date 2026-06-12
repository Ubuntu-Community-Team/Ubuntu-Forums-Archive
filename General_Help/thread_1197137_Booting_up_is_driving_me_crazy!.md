---
title: "Booting up is driving me crazy!"
date: 2009-06-25
forum: General Help
---

### Post by pinksprinkles on 2009-06-25
I decided to help my friend install a copy of their new Windows today and they wanted me to dual boot with Ubuntu for them. Installed Ubuntu in a separate partition then proceeded to install Windows. After Windows was installed, my GRUB wasn't coming up!

So I did the GRUB restore trick with the Live CD and GRUB came up again. I went into Ubuntu and tried to edit the menu.lst to help Windows come on again. I realized the mistakes I made now but I completely messed up my menu.lst file. I don't know how to fully restore it to how it originally was! I can't even edit the bootup screen choices because I made more than a hd(0,0) mistake!

And to make matters worse, my friend can't shut down her computer because I had to make a Super GRUB CD to help boot up the Windows partition (Super Grub didn't fix the problem either.)

When she restarts it, it'll load GRUB then say "unable to mount". Even if I fix the mounting with editing, the kernel and other things to fix are wrong and I don't know how to make them right!

What should I do? If I restore my old GRUB file, it'll be incorrect and will boot up wrong anyway due to mistakes I made editing it. On the other hand, I think I already used the backup boot.ini because my checkdisk didn't help Windows fix it's boot.ini again.

Should I just format both partitions, install Windows, then reinstall Ubuntu/Add in Windows boot to the menu.lst**correctly** this time? Or is there anyway to check out what my boot up menu.lst is SUPPOSED to look like so I can edit it?

---

### Post by merlinus on 2009-06-25
Why not post menu.lst so we can have a look?  And whilst you are at it, also results of:

```

sudo fdisk -l

```

---

### Post by Sub101 on 2009-06-25
Well if you install Ubuntu second the Grub should configure itself correctly without your help. 

However to fix your problem without having to reinstall, have you tried booting using a Live CD to edit menu.lst?

---

### Post by pinksprinkles on 2009-06-25
I'm not at that computer right now, but I do have an idea of what the menu.lst looks like. I know the rest is fine except for this part.

```
title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=366ef56a-2bf8-43ba-83d2-7094cf876145 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=366ef56a-2bf8-43ba-83d2-7094cf876145 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=366ef56a-2bf8-43ba-83d2-7094cf876145 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=366ef56a-2bf8-43ba-83d2-7094cf876145 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1 

```

Unable to fdisk -1 right now though. Everything seemed to be in tact though just having boot problems (Sorry I'm really new at Ubuntu lol)

And yes I tried editing menu.lst. The menu.lst that comes up is the recovered version of the menu.lst that I edited (and is very wrong), is there a way to restore or compile a menu.lst that was like the original (Before I wrecked it!)?

---

### Post by merlinus on 2009-06-25
You probably already know this, but menu.lst points to sda1 (hd0,0) for both linux and windows, and that will of course never work.

Do you know which partitions are which?

---

### Post by Tyke91 on 2009-06-25
heh... dunno what would happen if you did fdisk -1

fdisk -l  however would list out your partitions (L as in list)

---

### Post by pinksprinkles on 2009-06-25
> **merlinus said:**
> You probably already know this, but menu.lst points to sda1 (hd0,0) for both linux and windows, and that will of course never work.

Do you know which partitions are which?

I think 0,0 is my Ubuntu and 0,1 is my Windows (or something like that)

But a lot of the problem I'm having is 

```
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=366ef56a-2bf8-43ba-83d2-7094cf876145 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic
```

I'm really completely confused on what to put for kernel/root/initrd.

@Tyke- lol sorry I read that very wrong. I only have three partitions set up, and I remember the root/find stage1 stuff told me 0,0 for Ubuntu stuff (At least I think that's for Ubuntu stuff). I'll try fdisk -l tonight/tomorrow when I go over there again. I just want to have a general idea of how I could find out my old configuration for my menu.lst before I try to fix it again ^^;

---

### Post by Megrimn on 2009-06-25
Yeah, if it was me, I would just re-install windows first then ubuntu.  especially if you haven't been able to do anything with them yet.

---

### Post by merlinus on 2009-06-25
You can find out the UUID for the linux root partition:

```

sudo blkid

```Also remember to preface fdisk -l with sudo as well.

It seems to me that your situation may be fixable, but of course starting over might be the way to go, if you do not have lots of data to back up.

---

