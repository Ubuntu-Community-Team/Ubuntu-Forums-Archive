---
title: "WD external drive detected as a floppy"
date: 2011-02-21
forum: General Help
---

### Post by omg_linux on 2011-02-21
Greetings, ):P

Been using Ubuntu to extend the life of my hard drive. I'm not very familiar with the inner workings of Linux, but I know computers well. 

I've searched for an answer for a while, so I feel like this is my last option. 


My System: 
- Ubuntu 10.04, gnome environment. Dual boot XP.

Problem: 
- my external drive, WD essentials 2.2 TB, stopped working recently, about 6 months after installation of dual boot.

Facts: 
- still detected, though SMART does not detect it.
- XP still detects it - cant access files though. *
- Ubuntu now detects a floppy drive, which I do not have.
- power still working.
- have tried a few different USB cables.
- happened around the time of several software updates. Maybe paranoia.
- had trouble with music playback.

Hypothesis: 
- Drive is dying, cuz XP wont allow me in. *
- Something happened and it rolled back the drivers on the External HD.
- Somehow losing Voltage, though I dont know how. **

Have attempted:
- Disabling Floppy from bios.
- In Windows: disabling XP service pack 3, disabling Firewire 1394. 
- Different USB cables. **
- Disconnecting all USB devices, except External HD. **

Please help. 5 years of work (and music) are on the line. Thanks in advance! :D

---

### Post by JBAlaska on 2011-02-21
I does sound like your drive is dieing/dead, if XP Detects it, you might try putting the drive in the freezer overnight then hook it up and quickly download all your files off it if you can.

If it's the board in the enclosure that's bad, you can try cracking open the case and plug a SATA cable, Boot to Ubuntu as I think I remember hearing the drive is formatted as XFS,(The board translates it to NTFS) once you get the files off, you can try re-formatting it with whatever FS you want.

---

### Post by gerowen on 2011-02-21
> **JBAlaska said:**
> If it's the board in the enclosure that's bad, you can try cracking open the case and plug a SATA cable

Did this once with a WD Mybook.  Accidentally broke the USB connector while moving, and I failed epically at soldering, so my 500 GB external became a 500 GB internal and got replaced by a 1 TB Mybook.  The actual hard drive inside the enclosure is just a regular 3.5" SATA hard drive.

Edit: As a side-note Windows is horrible on hard drives.  Right now, even doing stuff, my hard drive light is off and pretty much stays off.  With 4 GB of RAM I guess Ubuntu just loads everything into RAM.  On the RARE occasion that I put in my Windows hard drive (Yes I keep them on separate drives) it's weird but I can be sitting at the desktop with nothing up and the hard drive light will just be constantly flickering on and off.  No viruses/malware, no scans running or updates installing, but the hard drive LED flickers.  After an hour of use, the Windows hard drive is normally burning hot.

---

### Post by coldraven on 2011-02-21
My 2c.
Take the drive out of it's enclosure and put it in a Sata dock. Then at the cost of around $30 you will know if it's the drive or it's controller.
If the drive is dead you are in for a big bill from a data recovery business
Google "sata docking station"

Edit: I just found this one, says it can handle drives up to 2TB so I'm now not sure this plan will work :confused:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153066](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153066)

---

### Post by psusi on 2011-02-21
Use an eSATA dock or just plug it in internally instead of USB.

You also should try running WD's diagnostic tool in windows.

---

### Post by JBAlaska on 2011-02-21
If it turns out to be the drive that's not spinning up, please don't discount my advice of putting it in the freezer overnight. I have rescued data off of MANY drives (A good portion of them WD's) with this method. It's worth a try before considering using a data rescue service that may cost you more than the data is worth. Bottom line it will not make matters worse, and just might do the trick.

Good luck!

**Edit:** After shaking the cobwebs out of my old brain :-), I now recall that only the **My Book World Edition** uses the XFS file system, if you have a standard WD My Book you can disregard my comment on it being formatted as XFS.

---

### Post by omg_linux on 2011-02-21
Thank you ALL for your replies!

I will attempt the following:
- friend's computer (MAC.... sigh)
- freeze
- sata

The reason for sata link being last is that its going to be a pain with my computer configuration. 

I think the "essential" files are about 1 GB worth, so 20 minutes should do the trick.

NOTE: i still find it very interesting that it reads it as a "floppy drive"...

---

### Post by gerowen on 2011-02-21
Note that some of the newer Western Digital hard drives have a weird partition on them that contains the WD backup and encryption software that shows up as a CD drive in Windows, this may be what you are seeing.

---

