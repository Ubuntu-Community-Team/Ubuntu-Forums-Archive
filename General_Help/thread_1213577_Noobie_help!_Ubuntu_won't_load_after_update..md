---
title: "Noobie help! Ubuntu won't load after update."
date: 2009-07-15
forum: General Help
---

### Post by relaxgman on 2009-07-15
Hi guys,

I am a newbie here. i Have been toying with ubuntu for only two days. I know nothing about the open source os that why I wanted to try. and now this....I already transferred my photos to my desktop. I refreshed my repos and I loaded the updates. After everything it ask me to restart my computer and this what i got. What should i do? Can i still recover my files in my desktop?[IMG]http://farm3.static.flickr.com/2598/3722867908_b2a0f7f586.jpg?v=0[/IMG]

---

### Post by manualqr on 2009-07-15
Yes, you can recover your files. Find an external hard drive, USB drive, or a CD.

Pop in your LiveCD and let Ubuntu load.

It should mount your HDD for you, but if it doesn't, try doing it manually (using the mount command on the partition you installed Ubuntu on). 

After you mount, pop in your backup media (USB, CD, external) and mount it.

Now you can copy files from your messed-up partition to a backup source.

(if anything isn't clear - especially the mounting stuff - just ask!, we'll help)

edit:
could you post details about your hardware?

---

### Post by relaxgman on 2009-07-15
> **manualqr said:**
> Yes, you can recover your files. Find an external hard drive, USB drive, or a CD.

Pop in your LiveCD and let Ubuntu load.

It should mount your HDD for you, but if it doesn't, try doing it manually (using the mount command on the partition you installed Ubuntu on). 

After you mount, pop in your backup media (USB, CD, external) and mount it.

Now you can copy files from your messed-up partition to a backup source.

(if anything isn't clear - especially the mounting stuff - just ask!, we'll help)

edit:
could you post details about your hardware?


Sir,

My hardware is:

c2d t5550
2gb ram
250gb hdd 



Sir can you give me a step by step? thanks

---

### Post by relaxgman on 2009-07-15
will i install another partition of ubuntu again?

---

### Post by manualqr on 2009-07-15
I'm not sure why your computer is behaving the way it is, but I think I can help anyways. It's my theory that during the update, Ubuntu installed a new version of the Linux kernel and messed with your bootloader.

When you turn your box on, GRUB (a bootloader) decides what OS to load. GRUB had recorded which partition (part of a disk) you installed Ubuntu on - so it finds the correct partition and starts the boot process for that OS. When you tried to boot into Ubuntu - the root filesystem could not be found.

Busybox (a rescue environment) is typically launched when all hell breaks loose in your system.. Like what's going on now.

So you've got 2 real options:
1. find out what the heck went wrong using busybox and fix it 
2. rescue your data and install a completely different OS in place of Ubuntu (windows, earlier version of Ubuntu, Fedora - perhaps)

I'll describe how you'd do both.

Option 1:
Your screenshot shows that GRUB believes Ubuntu is installed on (hd0,4) (note: could you post the first line of that message? I can't tell if it's a '4' or a '1'). This means that your Ubuntu partition is supposed to be in /dev/sda5 (or /dev/sda2). The issue is, GRUB can't find Ubuntu's root filesystem. You can tell pretty easily because it says so: "gave up waiting for root device". According to this: "ALERT!: /dev/<UUID> doesn't exist! dropping to shell!" - that UUID should point to your root FS. But it's wrong.

So at (initramfs), run these commands and post the output:

```

(initramfs) ls /dev | grep da
(initramfs) mkdir myhdd

```
*There should be no errors. If there are, something is seriously wrong.*

```

(initramfs) mount /dev/sda5 myhdd
(initramfs) ls myhdd
(initramfs) umount myhdd

```
*In the first command in this set, /dev/sda5 may not be found (or if it is, it may be the wrong device). Try other devices (sda1, sda2, sda3, etc.)*

```

(initramfs) cat /boot/grub/menu.lst | grep kernel | less

```
*This probably wont work. But if it does, post all of the information you see. (to get out of the scroll-screen, hit 'q')*

Depending on what happens, you can decide whether or not you want to follow through with option 1.

Option 2:
1. turn on your computer, pop in your Ubuntu install disk, and load Ubuntu in a LiveCD session
2. open a terminal (Accessories->terminal)
3. run these commands and post the output:
```

$ ls /dev | grep da
$ sudo mkdir myhdd
$ sudo mount /dev/sda5 myhdd
$ ls myhdd
$ umount myhdd

```

Depending on what happens, you can decide whether or not you want to follow through with option 2.

good luck - and ask questions if you have them

edit:
you may want to subscribe to this thread so you'll get an email every time someone posts something

---

