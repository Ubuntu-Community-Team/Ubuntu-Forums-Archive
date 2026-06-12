---
title: "extremely weird cd problem"
date: 2010-04-22
forum: General Help
---

### Post by devildoc5 on 2010-04-22
ok I am currently dual booting ubuntu and vista on an hp laptop.  All of the sudden my dvd rw drive stopped working in vista, checked ubuntu and same thing.  caused a whole bunch of needless problems for myself after this.  I have gotten back to the original starting point of this problem.  Here is the big issue though. 

BIOS says there is a cdrom drive attached
BIOS will not boot from dvd or usb
neither os will recognize the drive

things I have done thus far:
Delete upper and lower filters
Remove laptop hdd and place in desktop and reinstall vista
flash BIOS to newer version

None of this has worked.  When I say the drive is not recognized I mean that in vista for example, it does not show up in device manager AT ALL.

Anyone have any idea what so ever on how to fix this?

---

### Post by dcstar on 2010-04-22
> **devildoc5 said:**
> ok I am currently dual booting ubuntu and vista on an hp laptop.  All of the sudden my dvd rw drive stopped working in vista, checked ubuntu and same thing.  caused a whole bunch of needless problems for myself after this.  I have gotten back to the original starting point of this problem.  Here is the big issue though. 

BIOS says there is a cdrom drive attached
BIOS will not boot from dvd or usb
neither os will recognize the drive

things I have done thus far:
Delete upper and lower filters
Remove laptop hdd and place in desktop and reinstall vista
flash BIOS to newer version

None of this has worked.  When I say the drive is not recognized I mean that in vista for example, it does not show up in device manager AT ALL.

Anyone have any idea what so ever on how to fix this?

It's probably broken, replace the drive.

---

### Post by devildoc5 on 2010-04-22
sorry failed to mention.  I have swapped the drive and still have the same problems.  HP's answer seems to be "send it to us along with 300$ and we will get it working for you..."

And that also does not explain why I cannot boot from usb....

---

### Post by devildoc5 on 2010-04-23
anyone have any idea on what may cause this or if there is any sort of fix?

---

### Post by wilee-nilee on 2010-04-23
Is the dvd drive a usb plugin? if so check bios and see if usb functions are off.

---

### Post by devildoc5 on 2010-04-23
dvd drive is an internal slimline burner/player.  no usb at all, runs thourgh ata.


and usb functions appear to be on, however the BIOS is EXTREMELY minimalistic, so I cannot be certain, it just has boot options pretty much, that is the only place it mentions usb...

---

### Post by wilee-nilee on 2010-04-23
> **devildoc5 said:**
> dvd drive is an internal slimline burner/player.  no usb at all, runs thourgh ata.


and usb functions appear to be on, however the BIOS is EXTREMELY minimalistic, so I cannot be certain, it just has boot options pretty much, that is the only place it mentions usb...

Have you per chance used bleach bit or computer janitor. one of I believe beachbit messed up some dual functions between a dualboot of W7 and Lucid, user error of course, but I just flashed the bios as there was a newer version and all was fixed. I can't really confirm how it lost the functions nor do I remember exactly what they were, but it was nice to get the bios up to date as it fixed some other problems with the version I had.

Flashing bios is a possible bricking the computer situation so make sure if you do this you know what your doing.

---

### Post by eMJayy on 2010-04-23
That's pretty bizarre. This sounds like a hardware problem of some kind. 

Make sure that any data and power cables being used by the drive are undamaged. I've had instances where I thought a drive was damaged, only to find that I was unknowingly moving a faulty cable with the drive as I was testing it in another machine or using the faulty cable on another healthy drive.

---

### Post by devildoc5 on 2010-04-23
it is EXTREMELY unlikely that 2 drives have crashed.  I had a spare laying around that I pulled from an older laptop I recycled and it does not work either.  I have flashed the BIOs, it was the same version though, no new releases.  and if it was solely a CD error then why would I not be able to boot from USB when I could previously?

I have not used any of the two programs you listed, not even sure what they are so...

Drive uses some sort of a "extension card" or something to that effect...it changes it from SATA to the proper plugin from the slim line dvd player (not sure what the connection is looks kinda like a stacked dual SATA power cable in all honesty)  I suppose it is POSSIBLE that this "card" is not working, however that does not explain the usb problems as well, both happened at the same time, so I am relatively safe in assuming that they are both related to the same root cause. (hopefully)

---

### Post by eMJayy on 2010-04-23
It seems that the issue probably isn't the drive, but something on the motherboard.

The only suggestion I have left is to reset the CMOS if you can. That would reset the BIOS configuration back to factory settings. CMOS memory can get corrupted, resulting in malfunction of the motherboard. If that doesn't work, then you very likely have a motherboard issue.

---

### Post by devildoc5 on 2010-04-25
I have an hp pavillion laptop I have removed the cmos battery and also followed hps steps for a "soft reset" holding the power button with no power connected, however this does not seem to have actually reset anything....

---

### Post by eMJayy on 2010-04-25
> **devildoc5 said:**
> I have an hp pavillion laptop I have removed the cmos battery and also followed hps steps for a "soft reset" holding the power button with no power connected, however this does not seem to have actually reset anything....

When resetting the CMOS, did you leave the battery out for at least 30 minutes with the machine unplugged? Apparently, you may have to keep it out that long to get CMOS to clear.

---

