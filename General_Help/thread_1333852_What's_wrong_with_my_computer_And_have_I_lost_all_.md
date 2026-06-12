---
title: "What's wrong with my computer? And have I lost all my files?"
date: 2009-11-21
forum: General Help
---

### Post by potion on 2009-11-21
I've got a real mess on my hands. There are two issues:

First, when I start up the computer, just when I get to the login screen, the graphics go screwy and the system freezes. For a while now, I would occasionally get slightly screwed-up graphics at the same place, but I could use ctrl-alt-F1 and then ctrl-alt-F7 to sort of reset. Now that's not an option.

That's on Hardy, but I tried installing Karmic (and also running it as a live CD), and I get similar behavior. As soon as hi-res graphics come up, everything goes screwy and freezes up. I've tried all the recovery options available on the original Hardy install CD (repair broken packages, fix X), but nothing helps.

Do I need a new graphics card? Is it something else?

The second issue is kind of a heartbreaker for me. I've got most of my stuff backed up on an external hard drive, but there were a few things on the main system that I hadn't backed up. So I started up in recovery mode, dropped into root, and mounted the external hard drive manually:

```
sudo fdisk -l
sudo mkdir /media/external
sudo mount -t ext3 /dev/sdb1 /media/external
```

I didn't put anything else at the end of the mount command. I could see everything on the external hard drive, and I started moving the last few things over. And then, and I'm still furious at myself for this, I left the slash off the copy command:

```
cp -r home/jon/[source directory] /media/external/jon
```

Which overwrote the directory where I had everything saved. After a time spent feeling miserable about this, I resigned myself to the fact that I'd lost some of my stuff. A fair amount of it was still on the main system, so I started moving it all over to the external hard drive.

But it wasn't long before I got a message saying I was out of space. There wasn't much space left on the hard drive with all the backups on there, but there should have been tons and tons of space after I accidentally wiped it.

So I was wondering, is it possible that I didn't actually overwrite, but simply filled up what space there was, and the files are still there, and potentially recoverable?

Thanks a ton for any help you can give me.

---

### Post by fisheater on 2009-11-21
Sorry to hear your plight, I have recently lost all the stuff on my laptop - which wasnt much, just the stuff that wasnt backed up.

In reading on what I could do to recover my data, this beauty came up: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec). This may help you sort through the wreckage of your disk.

Good luck.

FE

---

### Post by potion on 2009-11-22
Thanks, fisheater. I'll give PhotoRec a try if I can get the computer working again. Maybe I can salvage some of the files on the hard drive. Sorry to hear you lost a bunch of stuff too.

---

### Post by fisheater on 2009-11-22
Check ([http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)) - this way you can run a liveCD session and use the tools to check what is on you HD. That way you dont have to install or fix your current OS - the more you use the HD the more data that can be over written...

Good luck

FE

---

