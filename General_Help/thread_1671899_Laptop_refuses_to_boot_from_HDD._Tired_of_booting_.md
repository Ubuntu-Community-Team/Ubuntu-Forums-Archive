---
title: "Laptop refuses to boot from HDD. Tired of booting from LiveCD"
date: 2011-01-20
forum: General Help
---

### Post by theITgirl on 2011-01-20
Okay, so for the past couple of weeks, I have been booting from an Ubuntu LiveCD. Here's why:

When I boot my computer (emachines E528 laptop), it gets to the BIOS loading screen (the one where you have the option to press a function key to get to the BIOS settings), then it goes to a black screen and looks like it is going to load GRUB, but instead of loading GRUB, the computer reboots. It does this endlessly, unless I insert a LiveCD. So, it's not the BIOS. That's good. When the Mint GUI (Linux Mint was the LiveCD I was originally using as I just happened to have it on hand) loaded for the first time, I checked all of the hard drive partitions and they all seemed to load fine. So, it's not a mechanical problem with the HDD. That's good.

At this point, I figured the MBR had become corrupted somehow. Now I wasn't really sure exactly where the MBR was, or how it all worked, but I was pretty sure that if I just reinstalled GRUB, everything would be hunky dorey. Unfortunately, I hit a road block when trying to install GRUB. That's not good. I am trying to follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=224351"), but I get the following error:

```
grub> find /boot/grub/stage1

Error 15: File not found
```So then I tried following the instructions [here]("http://ubuntuforums.org/showpost.php?p=1361177&postcount=26"), but I don't know how to tell which drive is sda1, sda2, etc. I'm guessing there's some terminal command to figure it out, but I don't know it and Google was less than helpful. I feel like something that basic should be easy to find, but I digress.

At this point, I am getting very close to backing up everything and reinstalling everything. Only problem with that is that I am not sure how to access the files on my Ubuntu partition as they are encrypted (I wrote down the key when I started it up, I just don't know how to bring up a prompt that will let me enter the key). I really don't want to reinstall and set everything back up, but if I have to I will.

So, I guess I just need to know how to tell which partition is associated with which sda#, or how to access the files in my encrypted Ubuntu home folder, or (hopefully) someone who can tell exactly what's going on from why I have posted and can give me instructions for fixing my problem.

Also, here's a breakdown of how my hard drive is partitioned. Not sure why, but I thought this might be helpful: [linky]("http://i.imgur.com/FvvDz.jpg").

**TLDR: **How do I tell which partition is associated to which sda#? How do I open my encrypted home folder from my Ubuntu partition? After reading my whole post, is there any further insight you could offer that I may have overlooked?

---

### Post by ellgor on 2011-01-21
Hi,

Just a suggestion, have you changed the boot option back to HDD in the BIOS options, in most cases F2 before it actually posts gets you there (actually as soon as any writing appears).

Regards, Ellgor.

---

### Post by cgroza on 2011-01-21
That tutorial is the right way to go. To find out which drive is sda1 etc. go to System -> Administration-> gParted and there you may recognize them by size or something else.

---

### Post by Hippytaff on 2011-01-21
The bootscript found [here]("http://sourceforge.net/projects/bootinfoscript/") should give you the info you need

---

### Post by tredegar on 2011-01-21
The links you were following were for what is now called "grub legacy"
Ubuntu now uses grub2 which is very different.
See [here]("http://ubuntuforums.org/showthread.php?t=1581099") for how to restore grub2

---

