---
title: "Graphic startup problems"
date: 2012-09-29
forum: General Help
---

### Post by ELMIT on 2012-09-29
I had trouble with overheating of graphic card, which leads to some unclean shutdowns. After cleaning the harddisk (fsck) one major problem remains:


When I start the system in normal mode (grub) I come to an annoying white screen with some unreadable letters in it. This was always so, but annoyes me now even more now, since more "writing" appears and it hangs there!

The writing is from left to right, black on white, partial a character and it seems to be mirrorred. I try to attach a picture, but it does not work to attach.

If I start the system in recovery mode (grub), I come to the recovery menu. Here I just need to continue! 
I will aslo come to the annoying white screen, but now I can switch to another console!
In another console (ALT-F2) I can use startx and I am in my system without Unity. Unity I can get back with a terminal and  unity --reset


How can I get my system fixed?

---

### Post by ELMIT on 2012-09-30
Does anybody has an idea where to start to track down that problem??

---

### Post by 2F4U on 2012-10-01
I guess you would get better responses if you would tell us your detailed hardware specs, including graphics card and what graphics driver you are using.
If you can get to a virtual console, you can also access the system log files contained in /var/log. These files may give a hint on what goes wrong during startup.

---

### Post by ELMIT on 2012-10-01
If I boot in normal mode it just stops, ... nothing I can see.

If I boot in recovery mode and continue, the screen shows a lot of information, which ends with these lines:

* Starting load fallback graphics devices   [failed]
* Starting Userspace bootsplash   [OK]
* Starting LgihtDM Display Manager   [OK]
* Stopping Userspace bootsplash    [OK]

There it stops forever, ...

With ALT-F2 I get a login
I used dmesg > dmesg.txt and attach it here the last 18k lines

startx starts now the graphic
opening a terminal and with unity --reset  I get the Unity as well.

I use GeForce 7600 GS
VBIOS 05.73.22.19.00
NVIDIA Driver Version: 295.40

What should I do next?

---

### Post by Eirreann on 2012-10-01
THIS!!  This is the problem that I made a billion of topics about ages ago when I was using my old laptop!!  Haha, so I wasn't the only one!
Although it wasn't exactly the same problem, it was that same weird white screen...  But yeah, when I had that issue, I eventually caved and completely re-installed Ubuntu.  When I did, it fixed the booting problem, but it replaced the Ubuntu boot logo to that nasty white screen (after the boot logo it worked fine).  Hey, after a while of that white-ness, does it start flashing random colours?

---

### Post by ELMIT on 2012-10-01
This white screen was already with 11:04 and did not change with 11:10 and 12:04, ... I got used to it, ... IF it disappears after a few seconds and works normal. ;-)

---

### Post by Eirreann on 2012-10-01
> **ELMIT said:**
> This white screen was already with 11:04 and did not change with 11:10 and 12:04, ... I got used to it, ... IF it disappears after a few seconds and works normal. ;-)

Huh.
Well I'm far from being an Ubuntu expert (in fact I'm probably the definition of a complete "noob") from what I understand from responses to my previous threads, the white screen is caused by, you guessed it, the video card.  My laptop had an ANCIENT video card, could barely run Ubuntu as it was.  Maybe your video card is too end-of-life to handle Ubuntu now... I hope that's not the case, but it's a possibility, I guess...

---

### Post by ELMIT on 2012-10-01
I would accept that theory if it would not work at all anymore, ... but why I can run it with the trick of recovery mode and continue?
It seems that in these two ways  of startup is something different what locks up normal and goes over with recovery mode.

While I was looking at the NVIDIA graphic card settings I found that my current card has only 256 MB RAM. I had "remembered" 512 MB RAM. 
I was already in the shop for a new card: 4GB DDR3 RAM, ... and if not soon my customer pay, then there might be already a 8GB available, .... 

BUT, till then I hope to get my current system to work properly, ...

---

### Post by Eirreann on 2012-10-01
> **ELMIT said:**
> I would accept that theory if it would not work at all anymore, ... but why I can run it with the trick of recovery mode and continue?
It seems that in these two ways  of startup is something different what locks up normal and goes over with recovery mode.

While I was looking at the NVIDIA graphic card settings I found that my current card has only 256 MB RAM. I had "remembered" 512 MB RAM. 
I was already in the shop for a new card: 4GB DDR3 RAM, ... and if not soon my customer pay, then there might be already a 8GB available, .... 

BUT, till then I hope to get my current system to work properly, ...
I think that you are thinking RAM there, video cards don't get much better than 4GB of VRAM, I've never seen, let alone heard of, a video card with 8GB (or perhaps I misunderstood you..).  My old video card has even less VRAM then yours does,128 MB if I recall correctly, and it could still *kind of* handle Ubuntu.  But yeah, if you can upgrade the video card, definitely go for it.  Switching from my laptop's GeForce FX Go5200 to my desktop's GeForce GTX 670 was an amazing transition, the better card really improved the Ubuntu experience!

---

### Post by ELMIT on 2012-10-03
Does anybody know how to fix that?

---

