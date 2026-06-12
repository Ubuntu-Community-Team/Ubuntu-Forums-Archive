---
title: "GRUB Error, no such partition"
date: 2009-10-29
forum: General Help
---

### Post by ImaginaryPixel on 2009-10-29
I get this grub error when booting

error: no such partition

Help please.  I have Windows 7 and Ubuntu 9.10 installed but I was never able to get GRUB to work to begin with.
I am unable to do anything right now.

here is a link to my other thread concerning GRUB not working.  I tried to reinstall it but now iit won't let me do anything [http://ubuntuforums.org/showthread.php?t=1304984](http://ubuntuforums.org/showthread.php?t=1304984)

---

### Post by VMC on 2009-10-29
Don't open another topic on the same subject. Now everyone will have to open that previous thread up just to see what's been done. In the future just reply from the same thread.

I did notice from the other thread that you tried to make linux partition bootable on the 58gb hard drive. Do you even know what happened with that?

Try this. Boot with livecd then open your ubuntu partition (sda6), and print out the "/boot/grub/grub.cfg" like so:

```
sudo cat /boot/grub/grub.cfg

```
 Also we need to see what you did with trying to make it bootable. Output this again:

```
sudo fdisk -l
```

---

