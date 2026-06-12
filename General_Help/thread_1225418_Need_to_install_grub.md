---
title: "Need to install grub"
date: 2009-07-28
forum: General Help
---

### Post by floydv on 2009-07-28
Grub got messed up when I was messing around, I have my system on my first hard drive had to install another distro to get on line on my second hard drive. I have done some reading but nothing seems to work so far.:confused::confused:

---

### Post by merlinus on 2009-07-28
Try this:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

---

### Post by philcamlin on 2009-07-28
> **merlinus said:**
> Try this:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

+1 reinstalling grub is your best bet 

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html) 

look there if you need any help :popcorn:

---

### Post by floydv on 2009-07-28
linux@linux-desktop:~$ sudo grub
[sudo] password for linux: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found

This did not work, however I did install Mandriva (but it is the 32bit) on 2nd hard drive and was able to boot back in, but I really need to figure out how I can go back to my Ubuntu grub if I can, or just leave Mandriva on the 2nd hard drive?,
Any suggestions regarding the grub and how I can re-install it? (let me try some things on the link you gave me tonite and see what happens)

---

### Post by floydv on 2009-07-29
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,4)
kernel		/vmlinuz-2.6.28-13-generic root=UUID=9efd55b5-06c8-42fb-88d8-7069e3af5d39 ro quiet splash 
initrd		/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,4)
kernel		/vmlinuz-2.6.28-13-generic root=UUID=9efd55b5-06c8-42fb-88d8-7069e3af5d39 ro single 
initrd		/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,4)
kernel		/memtest86+.bin  
savedefault
boot

The above system is the one I am having trouble installing the grub on, I jammed a copy of Ubuntu into a little space on my second drive and got it to boot, so by looking at this are there any suggestions of how you would go about putting grub back in this. It is like it is saying (hd0,4) however I tried this and it did not work. When I ran the installer I noticed there was no root partition, when I mounted the root partition it wanted to format so I scraped that idea. What it is I have done a lot of work on this system and don't want to lose it otherwise I would just start from scratch.

But all in all I could just leave the system on the second drive and continue like it is really, probably would not hurt anything just to do it this way. I gave the super grub tool a try also but still no luck with it either, but I am new to the game also and have a lot of learning to do.

---

### Post by floydv on 2009-07-30
> **merlinus said:**
> Try this:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

Alright I got it to work for me, had to figure where it was after some searching mine is on (hd0,4) after this I got grub back and everything is fine. I did manage to boot my system with grub messed up by using Super Grub, I had to modify the line to where I actually had to go to but it worked great.<SOLVED>:D
(thanks for the help guys)

---

