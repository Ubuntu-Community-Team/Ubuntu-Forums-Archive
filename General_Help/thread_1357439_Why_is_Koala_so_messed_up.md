---
title: "Why is Koala so messed up?"
date: 2009-12-17
forum: General Help
---

### Post by Struki on 2009-12-17
Ok my anger is a result of some hours trying to solve all of the problems that I have with the latest version of ubuntu - 9.10. I understand that it's a fresh release and it takes time to polish out all the bugs and stuff, but I' mean c mon!!! I'm a fresh user and I started with 9.04 while it was relative fresh release and still I had less issues with it. I'm not some dumb kid trying to run Halo 3 on linux, I do have some experience with computers (some 10-15 years or so). So some of my problems:

I can't mount drives, I got this error message:
[I]Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/sdb1[/I] 

I've used some tutorials to edit fstab file, so now my local partitions are mounted automatically, but if I plug in usb stick or a external hard, again I get the same error. 

My other problem is somewhat trivial but nevertheless, I link my folders located on ntfs partition via desktop links (I drag the folder to desktop and use link here option), so every time I reboot they end up rearranged to some default place on my desktop, and its always the icons linking to the ntfs partition (it's a non file system partition).

So I've posted my problems all over, but no one seems to answer, I don't know if my problems are so unique or complicated or it's that my english is so bad and no one understands me...

So anyone pls shed some light!

---

### Post by wojox on 2009-12-17
What happens when you try:

```
sudo mount -t vfat /dev/sdb1 /mnt/usb
```

---

### Post by Struki on 2009-12-17
This:

*mount: mount point /mnt/usb does not exist*

---

### Post by Techsnap on 2009-12-17
```
sudo mkdir /mnt/usb
```

Then try what wojox suggested.

```
sudo mount -t vfat /dev/sdb1 /mnt/usb
```

---

### Post by Struki on 2009-12-17
The above didn't help me much but i got an idea:

I've created directory:

*sudo mkdir /media/usb*

and then edited fstab and change the mount location to the folder i just made, so now my usb is mounted, but i got a feeling it's not the solution cause i still can manually mount or unmount any of the local partitions still getting the error:

[I]Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /media/disk[/I]

And what if I want to mount some other usb, I mean this was handeled automaticlly in 9.04

And how bout my icon problme?

---

### Post by xifer on 2009-12-17
Possibly the permissions on your mount points are not right
try sudo chmod 777 /media/usb for a start and maybe also on /dev/sdb1

For your other issue, I'm guessing this is a gnome session?

Right click on the icon and look for a lock panel option

---

### Post by Struki on 2009-12-17
> **xifer said:**
> 
For your other issue, I'm guessing this is a gnome session?

Right click on the icon and look for a lock panel option

Yes it is, but I'm not talking about panel icons, I'm having problems with icons located on my desktop

---

### Post by spiderbatdad on 2009-12-17
> **Struki said:**
> Yes it is, but I'm not talking about panel icons, I'm having problems with icons located on my desktop

A well documented bug, it has not been fix-released yet. As to your original question, I don't know the answer, but empathize.

---

