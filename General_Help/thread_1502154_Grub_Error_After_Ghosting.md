---
title: "Grub Error After Ghosting"
date: 2010-06-05
forum: General Help
---

### Post by leomoon on 2010-06-05
Hi, I'm having a very annoying problem that I can't figure it out.

I made a multi boot USB using Grub 2 and Grub4DOS (with some help of liveusb.info) which works perfectly fine cuz I tested it my self.

Now I want to GHOST an image of this multi boot so when ever I want to ghost it on another thumb drive, I can easily do it. But when ever I make the ghost image and I try to put it on another thumb drive and try to boot from the newly ghosted thumb drive to test it, it will give the error below:
loading.
error: the symbol `grub_puts_` not found
grub rescue>

I tried SO MANY different techniques to find what the problem is.
I tried making the multi boot using Ubuntu 9.04, 9.10 and 10.04 (which I think doesn't have anything to do with this but doesn't hurt to try!). I tried reghosting on the same brand and same size thumb drive and lots of other tries but I can't figure this out.

Can anybody tell me what the problem is OR what do you use to make an image of your bootable thumb drive?

Tnx.

---

### Post by _Mark_ on 2010-06-05
You will probably have to re install grub on to the usb after you have done the ghost, the easiest way of doing it is boot the livecd mount the usb and re write grub, their is a how to on the wiki for this here [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I followed it a while ago when i screwed up grub

---

### Post by Leppie on 2010-06-05
the best way to copy a pendrive is to use dd.
to create the copy:
```
[FONT=Verdana][SIZE=1][SIZE=2]dd if=/dev/hdx  of=/path/to/image[/SIZE][/SIZE][/FONT]
```
to write the copy to a new pendrive:
```
[FONT=Verdana][SIZE=1][SIZE=2]dd if=/path/to/image  of=/dev/hdx[/SIZE][/SIZE][/FONT]
```

---

### Post by leomoon on 2010-06-05
Tnx a lot for your replies. So here is another strange thing. I used to do this a couple of months ago and ghost it and it would work just fine. It might be that the new version of Grub can not be ghosted or something. But shouldn't Ghost copy EVERYTHING (and even boot sectors/MBRs)? Cuz that's what ghost is for!

---

### Post by Leppie on 2010-06-05
> **leomoon said:**
> I used to do this a couple of months ago and ghost it and it would work just fine. It might be that the new version of Grub can not be ghosted or something. But shouldn't Ghost copy EVERYTHING (and even boot sectors/MBRs)? Cuz that's what ghost is for!
i really don't know anything about ghost, i know that with the dd command especially pendrives can be easily copied.

---

### Post by leomoon on 2010-06-06
Tnx a lot. dd works perfect. :)

---

### Post by Leppie on 2010-06-06
you're very welcome.
sorry i can't help you with ghost.

---

