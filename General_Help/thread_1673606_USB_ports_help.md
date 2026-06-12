---
title: "USB ports help?"
date: 2011-01-22
forum: General Help
---

### Post by Claireiclees on 2011-01-22
I'm attempting (unsuccessfully thus far) to use the 'dd' command to move an iso file to a usb stick. I've seen examples,and pretty much get it, but I don't know what to put as the 'target' part. 
Most people seem to use things like 'sda2', or other such things, but I have no clue what this means, or any idea how to find out what my stick is called to the computer, I've tried all sorts of things. Everyone else knows what it is, but it doesn't seem to be documented anywhere.

In short, how can I find out what the target should be in my dd command for my usb stick?

Thanks for any help, I think it's a pretty simple question,
Claire.

---

### Post by ajgreeny on 2011-01-22
In terminal type ```
sudo fdisk -l
``` and the USB will show as /dev/sdx and contain partition(s) sdx# with increasing numbers depending on the number of partitions on it.

Look for the correct size in the first part of each disk's stanza to be sure you have the correct disk, or you could wipe out your hard disk install.

Why are you using dd?  There are other ways to do that job, Ubuntu USB Startup Disk Creator, Unetbootin, the latter of which will run on Windows if you don't yet have ubuntu installed.

---

### Post by Claireiclees on 2011-01-23
Thanks! 
Basically, I was trying to burn a minix 3 live cd/or usb just so I could get control of using dd. Soon I'll need to put the minix on a floppy disk so I can boot from it on my really old/dead computer, so this was just practice really. I burnt it to a cd, because I thought that would work at first, but then my dad said that the computer can't boot from it's cd drive so I was like "D:". Anyway, I can do it now, thanks for your help (:

---

