---
title: "New computer can not boot Lucid"
date: 2010-06-21
forum: General Help
---

### Post by ToxicBurn on 2010-06-21
Hi guys I just finished a upgrade 
 
I got a Gigabyte GIGABYTE GA-H55M-S2H, LGA1156, Intel® H55, DDR3 Motherboard 
 
G.SKILL Ripjaws Series 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model F3-12800CL7D-4GBRM 
 
and also a Intel Core i5-750 Lynnfield 2.66GHz 8MB L3 Cache LGA 1156 95W Quad-Core Processor 
 
As soon as i try to boot from USB image made with Unetbootin or the Live CD i get 
the splash screen with the Ubuntu logo and the white and red dots under the logo and then My monitor says going to sleep and thats it .
 
I also have a ATI HD 5770 but it works in 10.4 as of last week :)
 
I cant get past that 
 
a real bummer i cant run Ubuntu anymore
 
:confused:

---

### Post by Smart Viking on 2010-06-21
Hi.

Have you tried booting from a live CD, instead of usb? It might be that it will behave differently with a CD, my desktop per example is far from old hardware, but it wont even boot from usb. 

I wish you good luck, it is quite unfortunate that you can't get it to work, but hopefully it is pretty easy to fix with some easy twists and variations. One time i installed ubuntu on a PC that just resisted to boot form anything, i simple installed ubuntu on the harddisk with another machine, so that is also a solution. I hope this helps a little. :)

---

### Post by cheezburger on 2010-06-21
Try booting from live CD in 'safe graphics mode'
 You can do this by hitting F4 once the CD boots and selecting 'boot safe graphics'
If that doesn't work, go to edit command line (F6) scroll to the end and add "-- nosplash" (without the quotes)
Hope that helps!

---

### Post by ToxicBurn on 2010-06-21
no luck at all and in 10.4 if i Hit F4 there is no option for low graphics mode is there anything i can do ?
 
i really dont want to run windows

---

### Post by ToxicBurn on 2010-06-21
can anyone help please 
 
is there a way to get a log of whats stoping my live cd from booting.

---

### Post by S.R on 2010-06-21
Have you tried the alternate install? [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate) . I had a problem similar to yours when I installed my desktop and was successful with the alternate method.

I imagine you probably did but did you also check your BIOS settings?

---

### Post by ToxicBurn on 2010-06-22
I think it has somthing to do with my H55 chipset as i cant get any install method to work :( 
 
guess i am SOL untill 10.10

---

### Post by garvinrick4 on 2010-06-22
Look at link to see if any bugs reported and what is being done or done about it. 
I do know 3 things happen at get go, "ureadahead" and graphic drivers for "plymouth" and
"mountall". Your grahic drivers are getting there to start plymouth (splash screen) but nothing seems to mount. Go from there and look up in launchpad, got to be others with same set-up as you out there. Good luck.
And 10.10 is out in dailys. Alpha1

[https://launchpad.net/](https://launchpad.net/)

---

### Post by Gryph0n on 2010-06-24
I'm using the same motherboard with an i3, and have almost the same problem. For me, the DVI port works, but the VGA and HDMI ports give blank screens. (the problem is the screen i want to run it with only has VGA in). If you're running a 5770 though it might not apply...

---

### Post by thaspius on 2010-07-02
I have an almost identical setup
Gigabyte GA-H55M-S2H
Intel Core i5-750 Lynnfield 2.66GHz LGA 1156 95W Quad-Core Processor BX80605I5750
CORSAIR XMS3 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666)

I've tried usb,cds, and dvds. The livedisk, the install disk. havent tried the alternate disk yet. The disk just doesn't load. My bios startup just sits at the waiting for cd/dvd screen.

I've not ran 10.10 yet.

It does boot up a XenLive disk I had laying around. I'm planning to try 10.10, the alternate, CentOS live, and a couple other random disks.

---

### Post by thaspius on 2010-07-03
I just tried 10.04 alternate and it also would not boot. I also tried 9.10 and it wouldn't boot...

At this point I think I'll just go with CentOS...

10.10 isn't slated to be out until october from what i have seen.

---

