---
title: "Vista Laptop to Ubuntu/XP"
date: 2009-08-04
forum: General Help
---

### Post by dino1515 on 2009-08-04
I have a Compaq Presario V6000 laptop that is factory shipped with Vista that i have recently dual booted with ubuntu . (first time linux user)

My question is this. Is it possible now to fully install ubuntu over the top of Vista and then dual boot it with XP. I still need windows for my iPhone and also some games that i play however i hate Vista. Therefore i want xp instead.

I have been reading around and i have heard that my computer will not allow me to do this because of driver problems. is this correct?

---

### Post by martinbaselier on 2009-08-04
It is possible. The easy way is to install xp, then install vista (windows doesn't like it the other way around). When you've installed them both you can install linux. When you install xp you would need to spilt the hdd in at least two parts, or you won't have room for vista. Linux can create it's own partition without loss of data.

---

### Post by dino1515 on 2009-08-04
thankyou for the quick reply but i think you may have misunderstood, or maybe i have misunderstood you, my laptop came with vista but i want to get rid of it and replace it with xp dual booted with ubuntu!

---

### Post by NotJustANewbie on 2009-08-04
Install XP, whiping Vista.
Then install Ubuntu taking care at the partition stage to leave the XP partition alone. It will recognise it automatically :)

---

### Post by chrisinspace on 2009-08-04
> **dino1515 said:**
> I have been reading around and i have heard that my computer will not allow me to do this because of driver problems. is this correct?

You may have driver issues if Compaq doesn't provide XP drivers for your devices.  I would go to the support site, look up your laptop, and see what drivers are available before you make any changes to the system.  If you don't see the XP drivers listed there, you could check with the manufacturers of the individual hardware components.  The import thing is to investigate this first.

If you can find XP drivers and decide to make the leap, then start by booting from the XP disk.  Delete all partitions, then create a new partition for XP.  It will be easier to do the Ubuntu install if you leave some unpartitioned space for it to use, but if you don't, it's no big deal...the Ubuntu installer will help you carve out some space.  Install XP completely, then boot from the Ubuntu disk and set it up on a second partition.  It will see XP and help you configure the dual-boot parameters.  These steps assume you do not want to preserve anything from your previous installations.  If you follow them, you will be wiping your hard drive and setting up two clean installations.  Be sure to back up any data you don't want to lose.  

I have a 250GB hard drive, so I actually created a 3rd partition.  I formatted it as ext3 and installed the [ext driver for Windows]("http://www.fs-driver.org/") so it could read the partition.  That way I have a partition just for data that either OS can read.  If I ever need to reinstall one OS or the other, I just leave that partition alone and I don't have to worry about my data.

---

### Post by RJ12 on 2009-08-04
> **chrisinspace said:**
> You may have driver issues if Compaq doesn't provide XP drivers for your devices.  I would go to the support site, look up your laptop, and see what drivers are available before you make any changes to the system.  If you don't see the XP drivers listed there, you could check with the manufacturers of the individual hardware components.  The import thing is to investigate this first.

If you can find XP drivers and decide to make the leap, then start by booting from the XP disk.  Delete all partitions, then create a new partition for XP.  It will be easier to do the Ubuntu install if you leave some unpartitioned space for it to use, but if you don't, it's no big deal...the Ubuntu installer will help you carve out some space.  Install XP completely, then boot from the Ubuntu disk and set it up on a second partition.  It will see XP and help you configure the dual-boot parameters.  These steps assume you do not want to preserve anything from your previous installations.  If you follow them, you will be wiping your hard drive and setting up two clean installations.  Be sure to back up any data you don't want to lose.  

I have a 250GB hard drive, so I actually created a 3rd partition.  I formatted it as ext3 and installed the [ext driver for Windows]("http://www.fs-driver.org/") so it could read the partition.  That way I have a partition just for data that either OS can read.  If I ever need to reinstall one OS or the other, I just leave that partition alone and I don't have to worry about my data.

I completley agree I think its Sata drives that XP cant use or recognize

---

### Post by King_Ragger on 2009-08-04
I have a friend with a V6000 laptop and he couldn't find XP drivers for his WLAN card. Hopefully you have a different wireless card than him or you will be forced to get an expansion card or be stuck with an Ethernet cord.

[edit: XP (my XP anyway) can recognize both SATA 150 and SATA 300 hard drives with no problem. But if its an older install it won't recognize more than a certain amount of space on an hdd, I think it's 132gb but don't quote me on that. SP2 fixed that issue.]

---

### Post by FIONEX on 2009-08-04
Few things that you need to figure out before you do anything:

Which XP cd do you have?  It has to be the SP2 install CD because you need SATA drivers in the XP installer in order to detect your harddrives.

Are there XP drivers for ALL your hardware?  Figure out what hardware you have and go looking for XP drivers first.

Why do you need windows for the iPhone?

---

### Post by dino1515 on 2009-08-04
Thanks everyone this will definitely help,

 and FIONEX is there a way to sync the iphone with Linux, because if there is i no longer will need windows and this will solve all my problems???

---

### Post by dino1515 on 2009-08-04
> **FIONEX said:**
> 

Why do you need windows for the iPhone?


Is there a way to sync the iphone with linux????

---

### Post by chrisinspace on 2009-08-04
> **dino1515 said:**
> Is there a way to sync the iphone with linux????

Not that I know of.  I was given an iPod Touch as a gift and I was not able to find a way to sync it in Linux.  I know Songbird is working on it, but last I heard they aren't there yet.  I haven't researched the issue in a while, though, so maybe something has come out recently.

---

### Post by finch127 on 2009-08-04
Well as to your SATA problem, I know for some computers there is an option in the BIOS that allows XP to make use of them. I forget what it is but it is SATA related and a friend of mine had this problem so we changed the option and it worked just fine. Problem was, XP wouldnt recognize the drive during install, so once we changed the option it worked fine. I think the option was named "Use SATA Driver" or something with "IDE/SATA Driver" something like that.

---

