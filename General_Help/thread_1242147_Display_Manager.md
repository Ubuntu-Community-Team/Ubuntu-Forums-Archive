---
title: "Display Manager"
date: 2009-08-16
forum: General Help
---

### Post by harecanada on 2009-08-16
I have had a flickering screen problem and can't seem to figure it out. I looked around on the forums and seems a lot of people have a similar problem without a solution. If I am not having a flickering problem and I click on System>Preferences>Display my screen flickers and won't stop and I have to reboot my system. When I reboot it takes a few minutes and it flickers all the while it is rebooting. Once it's done things work OK to a degree. If I turn Compiz off, I can't turn it back on. I have to reboot again.   Does anyone want to help tackle this problem and help a bunch of people out?
harecanada

---

### Post by RedSingularity on 2009-08-16
Which graphics card are you using?

---

### Post by harecanada on 2009-08-17
I'm using  ATI Technologies Inc RV630 [Radeon HD 2600XT]
harecanada

---

### Post by RedSingularity on 2009-08-17
Did you install drivers?

---

### Post by harecanada on 2009-08-17
Yes. ATI/AMD proprietary FGLRX graphics driver.
harecanada

---

### Post by RedSingularity on 2009-08-17
Ok try reconfiguring the Xserver.

Use this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by RedSingularity on 2009-08-17
Oh and In System>Administration there may be a ATI configuration editor.  Try using that instead of the default ubuntu "Display manager".

---

### Post by harecanada on 2009-08-17
shadow121 Please tell me you know how to reverse that command you told me to use!! My system just got hosed when I put that command in. All I have is a black screen with a few lines at the top of it. The keyboard does nothing and I tried to do a recovery and got nothing. I need help. I'm on my wife's system. Contact me right away,
harecanada

---

### Post by RedSingularity on 2009-08-17
Ok boot into the recovery console and use this command to uninstall the graphics driver which is giving you a problem.


```
sudo apt-get autoremove xorg-driver-fglrx
```

Then reboot the system.

---

### Post by harecanada on 2009-08-17
WHOA! That got me back on. Sheer panic for a while. Thank You. 
I don't think Compiz is turned on any more but that's OK. The flickering doesn't seem to be happening but I won't know until I reboot. I'll get back to you.
harecanada

---

### Post by RedSingularity on 2009-08-17
You are now working off the open source drivers not the proprietary.  Unfortunately they do not offer 3D support yet...for things like compiz.....but it is stable nonetheless.

---

### Post by RedSingularity on 2009-08-17
Oh i thought you may want to know, you can receive real time help from the people on the Ubuntu IRC channels.  They are under the channel "[B]#ubuntu". 

[/B]In many cases you can solve your problem much quicker there because you are chatting to other users in real time.

---

### Post by harecanada on 2009-08-17
shadow121,
So reboot is OK except for a couple of problems.
1] I get a screen that says the following:
   Main Processor: AMD/Athlon(tm) 64x2 Dual Core Processor 5600+

Memory Testing : 3144704K OK      (Installed Memory: 3145728K)

SATA 0 : ST 3500620AS   DE 12
SATA 1 : HL-DT-ST DVD+/- RW GSA-H73N C106
SATA 2 : NONE
SATA : 3 NONE

DISKETTE drive 0 seek failure



Strike F1 to retry boot, F2 for setup utility
06/02/2008 -1.0.12

I don't know what this means, but when I "strike F1" it reboots and works fine. I think it is looking for a Diskette drive and I don't have one.

2] When its shutting down and starting up the Ubuntu logo is very basic and plain color as if I'm using 8bit color or something. Not a big problem but I don't understand why it does it.

harecanada

---

### Post by RedSingularity on 2009-08-17
Did you check your BIOS setup to make sure that you hard drive is the first boot priority and not a floppy or usb device?  

The lousy color is due to the Open source drivers.  They lack the potential of the proprietary ones.  Of course the Proprietary ones were giving you other problems.  Its really a decision of which problems are worse in some cases.

Also you should know......ATI cards have been known to give linux users problems.  They are still developing a good driver for ATI in linux.  For now some cards work better than others.  I had a laptop with a ATI installed which i never got to work.  Hopefully in the near future this will be fixed because personally i like a ATI and AMD.  For now though Nvidia is the recomended way to go with linux.  Even a cheap card will do wonders if you happen to have some spending money laying around to pick one up with.

---

