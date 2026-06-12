---
title: "can't boot from CD - pulling my hair out"
date: 2010-10-29
forum: General Help
---

### Post by jeebustrain on 2010-10-29
OK, I'll start off by saying that I've used Ubuntu for a while now and I've installed it on quite a few machines. This problem is really perplexing. I've got a machine that I wiped (hand built) that's had every version of Ubuntu on it since 8.10 - installed with no problem. The previous incarnation had Ubuntu Studio 10.04.

So I've got a fresh clean HDD. I download (via torrent) the standard 10.10 x64 disk. I boot from the CD and it just hangs at the ISOLINUX bootloader message. That pops up and the CD drive just spins down and nothing happens after that. So I do an MD5 sum on the iso checks out fine. I try the Alternate install CD, same problem. MD5 sum checks out fine on that too. I put the same failing CD in my laptop and it boots straight to the Install Menu.

So I grab a Fedora 13 and a CentOS ISO and burn both of those to CD. In this machine, both of those CDs boot absolutely fine and go straight to the live CD desktop.

This PC has 2 optical drives, a SATA bluray drive and a PATA dvdrw drive. I get the same behavior on both drives. I've updated the BIOS on the motherboard (ASUS). I've tried to hit escape and hold down both shift keys while the thing is booting and neither have any effect. 

The only thing I haven't tried yet is to burn another 10.04 CD to see if that works. 

Is this karma for last week when I heard that Katy Perry song on the radio and I didn't change the station right away? Has anyone experienced anything like this?

---

### Post by janpol on 2010-10-29
Could you give more details about your hardware?


I think you learned the lesson tho, next time....change the station xD

---

### Post by lindsay7 on 2010-10-29
Have you tried the 32 bit disk?

---

### Post by jeebustrain on 2010-10-29
> **janpol said:**
> Could you give more details about your hardware?


I think you learned the lesson tho, next time....change the station xD

Sure - 
Athlon XP 5000+
M3A32-MVP Deluxe mobo
4GB OCZ Platinum DDR2-1066
500GB WD Caviar 7200
PNY Geforce 9600 GT
LiteOn PATA DVDRW
ASUS SATA Blu-Ray Reader

---

### Post by jeebustrain on 2010-10-29
> **lindsay7 said:**
> Have you tried the 32 bit disk?

I have not tried that - I will add that to my test though.

---

### Post by malcmail on 2010-10-29
Not what you would call a perfect solution but I had a similar problem before and installed the server version. Then added the bits and pieces from the desktop installation that I needed as I went along. If you are really stuck.

---

### Post by Lamez on 2010-10-29
This seems like a retarded response, but I have had something similar happen to me, update your burners firmware.

Also are you using the same kind of CDs on both OSs? 

Also have you tried the disc on another computer?

---

### Post by jeebustrain on 2010-10-29
> **Lamez said:**
> This seems like a retarded response, but I have had something similar happen to me, update your burners firmware.

Also are you using the same kind of CDs on both OSs? 

Also have you tried the disc on another computer?

yea, actually I tried it on a different PC as well (32bit no less) and the CD booted up just fine, right to the menu. I've also tried multiple burns of 2 different CD types - both have worked fine for me in the past.

I'll look into the firmware option. Thanks for the idea.

---

### Post by jeebustrain on 2010-10-29
> **malcmail said:**
> Not what you would call a perfect solution but I had a similar problem before and installed the server version. Then added the bits and pieces from the desktop installation that I needed as I went along. If you are really stuck.

I might end up doing something like that. Actually, the route that I was thinking of taking as a last resort would be to just install 10.04 on there (which did work, at least at one time) and do a dist-upgrade to the current version.

---

### Post by jonnywombat on 2010-10-29
Just a thought, and it don't solve your problem, but as a work around can you not simply install from a usb pen drive instead?

---

