---
title: "Atom D510 wont work with any 9.10! Help!"
date: 2010-02-01
forum: General Help
---

### Post by tylerhardy on 2010-02-01
Hey All, 

So I've purchased the Intel BOXD510MO Intel Atom D510 to build a personal file server.  Having major issues, whenever I try to load or boot or whatever from a 9.10 variant, nothing happens.  I've tried various methods and none have worked. What I've tried so far:
 -Ubuntu 9.10 server
 -9.10 IPIA
 -9.10 alternative
 -9.10 live (wont even boot to the live os)
 -xubuntu 9.10
 -xubuntu 9.10 from a flash drive
 -ubuntu 9.10 from a flash drive
     -installed 9.04 ubuntu and then upgraded to 9.10 (9.04 loads and installs just fine. however after upgrading to 9.10 nothing happens just a black screen after install and reboot.  tried various boots and nothing works).  
     Windows 7 loads and installs just fine, same with any 9.04 variant.  I've tried to search online and it seems that it is only me with this issue.  please help!

---

### Post by alex04210 on 2010-02-09
> **tylerhardy said:**
> Hey All, 

So I've purchased the Intel BOXD510MO Intel Atom D510 to build a personal file server.  Having major issues, whenever I try to load or boot or whatever from a 9.10 variant, nothing happens.  I've tried various methods and none have worked. What I've tried so far:
 -Ubuntu 9.10 server
 -9.10 IPIA
 -9.10 alternative
 -9.10 live (wont even boot to the live os)
 -xubuntu 9.10
 -xubuntu 9.10 from a flash drive
 -ubuntu 9.10 from a flash drive
     -installed 9.04 ubuntu and then upgraded to 9.10 (9.04 loads and installs just fine. however after upgrading to 9.10 nothing happens just a black screen after install and reboot.  tried various boots and nothing works).  
     Windows 7 loads and installs just fine, same with any 9.04 variant.  I've tried to search online and it seems that it is only me with this issue.  please help!



[COLOR="DarkRed"][SIZE="4"]I have the same problem. I have also tried ubuntu 8.04 LTS server.
Is there any way to launch ubuntu on INTEL ATOM D510?[/SIZE][/COLOR]

---

### Post by Menthu_Rae on 2010-02-09
Have you guys tried the 10.04 alpha? You may need a newer kernel (such as that in 10.04) for support of the D510.

---

### Post by alex04210 on 2010-02-10
> **Menthu_Rae said:**
> Have you guys tried the 10.04 alpha? You may need a newer kernel (such as that in 10.04) for support of the D510.

10.04 isn't working, too (((

and moblin - the same

xubuntu adm64 - the same

**any ideas?**

---

### Post by 3rdalbum on 2010-02-10
Ubuntu does not include a driver for the "Poulsbo" graphics chipset, for a couple of reasons that apparently are being worked on. Try a different distribution, such as Fedora.

I'm assuming that "blank screen" is your problem? You weren't very clear with exactly what your problem was, at what point it all failed.

---

### Post by murderslastcrow on 2010-02-10
Yes, it would be a good idea to try a different distribution for the moment being. Also, make sure that you're not using a 64-bit version of Ubuntu if this processor only supports 32-bit operating systems.

---

### Post by alex04210 on 2010-02-10
> **3rdalbum said:**
> Ubuntu does not include a driver for the "Poulsbo" graphics chipset, for a couple of reasons that apparently are being worked on. Try a different distribution, such as Fedora.

I'm assuming that "blank screen" is your problem? You weren't very clear with exactly what your problem was, at what point it all failed.

Yes! 'blank screen' when reboot after it's been installed or when starting live ubuntu.

[SIZE="5"]I tried Pmagic, it's worked out! [/SIZE]but I've got some problems with net. ethernet did't work

---

### Post by alex04210 on 2010-02-11
I installed Fedora 12 on Atom D510!
It runs OK!

goodbye ubuntu! :cry:

---

### Post by kircher on 2010-04-19
Sorry to bring up an oldish thread, but am I lead to believe Atom D510 doesn't work at all with ubuntu 9.10 and 10.04? ie There is no support for the integrated GPU?
I found this video which is evidence to the contrary
[http://www.youtube.com/watch?v=u9EFmW_cuO0](http://www.youtube.com/watch?v=u9EFmW_cuO0)

I wish to build a low power atom based 'nettop' and run ubuntu on it, but if this is the case I might have to think again. I don't really want to use Windows 7.

---

### Post by cascade9 on 2010-04-19
Apparently, it doesnt run on 10.04..yet...but it does on 9.10 down to 8.04-

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

BTW, even if ubuntu doesnt run on something, you have choices other than windows- lots of distros out there.

---

### Post by kircher on 2010-04-19
Thanks for that info.

I realise there are other distros, I shouldn't have mentioned windows 7. I have tested several other distros and always come back to Ubuntu. The size of the repositories is one reason why, but I liked Fedora 12 too.

---

### Post by Rusna on 2010-04-25
Have you noticed that Intel has released [a new BIOS]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18939&ProdId=3196&lang=eng") for D510MO on 14.4.?

---

### Post by AlexanderDGreat on 2010-04-28
This sucks, I'm planning to buy this motherboard, now I don't want to THROW AWAY MY MONEY DOWN THE DRAIN if Ubuntu Lucid Lynx won't work on this.

I've seen this far too many times, I buy hardware and Ubuntu rejects it totally! USB soundcard, 3-in-1 Canon scanners, now Intel Atom D510 mobo and cpu's... Sad. :(

---

### Post by AlexanderDGreat on 2010-04-28
To everyone reading this thread, I found this:

[http://blog.aleutia.com/2010/02/21/fanless-atom-d510-processor-in-aleutia-d1-and-p1-tomorrow/]("http://blog.aleutia.com/2010/02/21/fanless-atom-d510-processor-in-aleutia-d1-and-p1-tomorrow/")

It says, 

> Unfortunately it does not work with Ubuntu out of the box &#8211; **you have to flash the BIOS at least for 9.10** &#8211; but of course Aleutia does that for you before shipping it as part of our free OEM install of 9.10.

Can you please try this and will it work? First of all, how do you flash a bios the Ubuntu way? Second, anyone tried this with the final version of Lucid Lynx? Thanks. :)

---

### Post by fild on 2010-05-04
> **AlexanderDGreat said:**
> 
Can you please try this and will it work? First of all, how do you flash a bios the Ubuntu way? Second, anyone tried this with the final version of Lucid Lynx? Thanks. :)

Don't know if this helps but, I've been using Xubuntu 9.10 on a BOXD510MO motherboard with a D510 cpu.  Had a few problems getting the video going but it worked.  I upgraded to the final release 10.04 and it all stopped..... What I found was reboot with no monitor attached and Xubuntu errors, reattach the monitor and a small window appears that allows a Restart of the Xserver, this works and I get normal resolution and everythings is fine.  I tried the latest BIOS upgrade from Intel, that didn't help.
btw, the D510 cpu ticks along nicely in Xubuntu.

---

### Post by LolitaRainking on 2010-05-07
I'm running Ubuntu 10.04 on a Gigabyte GA-D510UD (with an Atom D510 with intel chipset) without any problems except that Nautilus used 100% of the CPU. That was easily fixed by uninstalling it and replace it with Thunar. So the rumors about Ubuntu not running on an Atom D510 seems a bit over-exaggerated.

---

### Post by jap1968 on 2010-05-28
Ubuntu 10.04 runs fine on Intel D510MO motherboard.

BIOS has not been updated at all. In fact, I think that my board has the first BIOS version of this board:

     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 4
          version: MOPNV10J.86A.0115.2009.1006.2145 (10/06/2009)

I am using the 64 bit edition, and I was able to install 10.04 without any problems. Everything is working properly. Only limitation is the intel video driver: The system uses the i915 driver while having a much more powerful hardware.

$ uname -a
Linux d510 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

---

### Post by grambo123 on 2011-05-15
To update the BIOS you have to install first.  The way I solved the problem is change the graphics set p in the BIOS and it installed like a charm using 10.10 64 bit.  Its not like you buy an ATOM to run graphics anyways.  
 
Pointless setup correct me if I am wrong 80W p.s. with ATOM processer and NVidia graphics card to play World of War Craft ??

---

### Post by Perfect Storm on 2011-05-16
Necromancing. Thread closed.

---

