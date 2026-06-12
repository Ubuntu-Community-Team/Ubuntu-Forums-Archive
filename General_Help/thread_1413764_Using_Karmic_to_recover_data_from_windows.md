---
title: "Using Karmic to recover data from windows?"
date: 2010-02-22
forum: General Help
---

### Post by Bill D on 2010-02-22
Hello, I have a full Ubuntu 9.10x64 install on an external hard drive and I was recently asked by a friend who has a laptop running 32 bit vista if I might be able to help him in recovering anything from pictures to Quick Books files. He believes the hard drive is corrupted. His laptop is an HP with less than 2 gigs of ram, and he is not sure about the motherboard/chipset. It may or may not support x64.  He went out and bought an iMac the other day so he wouldn't need to deal with not having a working computer. :(

Now I have 2 questions. The first being, I am wondering if my x64 install will still be able to run if I tried booting to it from his computer in the event that the chipset that does not support 64 bit architecture, or do I need to revert to a 32 bit install?

My instinct/what I perceive to be the obvious answer, is that yes, my x64 install should/will be able to boot via the bios.

My second question is: how do I go about loading Ubuntu once the external is plugged into the iMac?

Thanks in advance!

---

### Post by 0nullun0 on 2010-02-22
Don't bother using your external hard drive to boot your friend's system. Instead, connect your (or another) external hard drive or flash media, boot his system from an Ubuntu LiveCD, browse his corrupted hard drive (assuming it'll spin up), and move the files he's after to the external media. 

Hope this helps. 

0nullun0
m

---

### Post by Bill D on 2010-02-22
I've tried creating a live disk with Create USB Startup  Disk in Ubuntu and I've also tried creating a live disk with  Unetbootin in order to test out a new release

They both work to create the live disk for me, but I still can not access/mount the HDD of the computer I am working with at the time.

---

### Post by C.S.Cameron on 2010-02-23
You should be able to find the hard drive on the left side of file browser or under filesystem/media.
Or perhaps the hard drive is bricked.

---

### Post by Bill D on 2010-02-23
So I managed to create a live disk on my USB drive, and I have successfully managed to access the corrupted hard drive. Is there any way to search for image files (jpg, png, gif etc) without manually trying to go through every folder and locate them that way?

---

### Post by Herman on 2010-02-24
Just right-click on your top panel and click 'Add to panel'.
Scroll down to around half way down the list of programs you can add to your panel and look of the 'search for files' program, it has an icon that looks like a magnifying glass.
Add it to your panel and launch it.

You should be able to find all your files with that, it's easy to use and it works really well.

---

### Post by Herman on 2010-02-24
If you are in a hurry you can create an empty directory in your /home/username folder and call it 'rescue'.
Then try out these commands,
```
find /media/Windows -iname "*.jpg" -exec cp {} ./rescue \;
``````
find /media/Windows -iname "*.png" -exec cp {} ./rescue \;
``````
find /media/Windows -iname "*.gif" -exec cp {} ./rescue \;
```Where: Your mount point is called /media/Windows, if not then please adjust the file path appropriately.
You can also type a different file path for the rescue directory, if you wish you could just copy all your files right into Pictures instead, for example. Or into another mounted drive.

It's often faster to use Linux commands instead of the GUI when you want to get things done quickly, easily and perfectly.

---

