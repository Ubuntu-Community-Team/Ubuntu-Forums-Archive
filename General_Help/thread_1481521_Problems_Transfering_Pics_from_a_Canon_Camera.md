---
title: "Problems Transfering Pics from a Canon Camera"
date: 2010-05-12
forum: General Help
---

### Post by galobuntu on 2010-05-12
Hi there.

I have a **Canon Powershot A470** digital camera and can't get to transfer the pictures from it on **Ubuntu 10.04**. When I had Ubuntu 9.04 I imported pictures from the same camera without any problems. I considered that the problem could be the camera itself or the USB cable, but I have just accessed my pictures from that camera using Windows Vista.

Basically, what I have tried is 1) connecting the USB cable to the camera and the computer; 2) set the command button to the playback position; 3) turn on the camera. Using Windows Vista, this series of procedures opens the camera folder (as a flash drive) on Windows Explorer and this is what used to happen when I was using Ubuntu 9.04. I expected this to happen using the Lucid Lynx, but I didn't get even close. I even opened the Home Folder to see if something new showed up there when I hooked up the camera and turned it on.

Since I'm new with Ubuntu (especially the Lucid Lynx), I don't know what I'm doing wrong. I have read that sometimes we have to mount devices in order to get them to communicate with the computer. Is this one of those cases? If so, how do I do it? Does anyone else have the same model of digital camera? How do you guys transfer the pictures to your Ubuntu-based system?

Thanks a lot. I hope someone can help.
:P

---

### Post by t0p on 2010-05-12
I would suggest you do the following:

[LIST]
[*]Connect camera to computer with USB cable;
[*]Switch on camera;
[*]Launch F-Spot;
[*]In F-Spot, click to Import;
[*]You get a list of possible devices to import from: choose the camera.
[/LIST]
If that doesn't do the trick, report back with error messages.

---

### Post by gldearman on 2010-05-12
When you connect and turn on the camera, it should mount.  The place where it mounts isn't in your home directory, though.  It will likely be a subdirectory in /media/

Try navigating to /media/ in Nautilus (the file Browser) and see if there are any subdirectories there.  My camera usually mounts as /media/disk/ or some variation of that.  Your picture files would be in there (maybe in another subdirectory, depending on the camera), and you can move them just by selecting and dragging to your home directory.

---

### Post by galobuntu on 2010-05-12
It totally worked the way t0p suggested and it was very easy. 

However, I couldn't find the directory where it mounts. Gldearman, I tried what you said, but I wasn't able to find the camera under "media". All I found was an empty folder. 

Thank you, guys. It was very helpful and my problem is now solved.

---

### Post by bcooperb on 2010-06-02
Apparently this is an actual bug with Ubuntu 10.04

[https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/581352](https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/581352)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557232)

I have a canon 50D and Ubuntu 9.04 would see it, let me browse it, and copy files over.

I did get my files off using F-Stop. But I like to do it manually...hopefully this will get fixed soon.

---

