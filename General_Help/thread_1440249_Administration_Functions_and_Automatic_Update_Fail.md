---
title: "Administration Functions and Automatic Update Fail to Work"
date: 2010-03-27
forum: General Help
---

### Post by mikeprosceo on 2010-03-27
I am using Ubuntu 8.04. Most of my Administration functions have stopped working. If I click on Hardware Drivers, Hardware Testing, Log In Window, Software Sources, Synaptic Package Manager, and Windows Wireless Drivers my pointer turns into the timer wheel, so I know it is working, but then it just disappears and nothing happens.  When I click on Update Manager my computer freezes.  If I try to update through the red Updates Available arrow at the top of my screen my computer freezes.  I can update through terminal but the red arrow never goes away.  I also have 17 updates that won't update.  I have tried them one at a time through terminal but they just freeze the computer. The only way to unfreeze it is to shut the computer down.  Please can anyone help me get these functions back?  I am a basic novice but follow instructions real well.  Thank you for your help. - Mike Prosceo

---

### Post by philinux on 2010-03-27
> **mikeprosceo said:**
> I am using Ubuntu 8.04. Most of my Administration functions have stopped working. If I click on Hardware Drivers, Hardware Testing, Log In Window, Software Sources, Synaptic Package Manager, and Windows Wireless Drivers my pointer turns into the timer wheel, so I know it is working, but then it just disappears and nothing happens.  When I click on Update Manager my computer freezes.  If I try to update through the red Updates Available arrow at the top of my screen my computer freezes.  I can update through terminal but the red arrow never goes away.  I also have 17 updates that won't update.  I have tried them one at a time through terminal but they just freeze the computer. The only way to unfreeze it is to shut the computer down.  Please can anyone help me get these functions back?  I am a basic novice but follow instructions real well.  Thank you for your help. - Mike Prosceo

Open a terminal.

```
df -h
```

Post back what it says.

---

### Post by mikeprosceo on 2010-03-27
mikeprosceo@mikeprosceo-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              13G  3.9G  7.9G  33% /
varrun                442M  124K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   64K  442M   1% /dev
devshm                442M   52K  442M   1% /dev/shm
lrm                   442M   40M  403M   9% /lib/modules/2.6.24-24-generic/volatile
/dev/hda1              52G   18G   35G  34% /media/hda1
/dev/hda2             8.4G  7.1G  1.3G  85% /media/hda2
/dev/hda3             1.1G  663M  366M  65% /media/hda3

Above is what I get. - Thanks

---

### Post by tkoco on 2010-03-27
I take it that your system was operating ok for some time and recently developed this "freezing" problem. A desktop lockup can be caused by hardware problems. Unbeknownest to me, one of my systems had a problem developing on the motherboard of the computer. (a few months ago) It turned out to be the SATA port driver chip was going bad. I cloned the hard drive from the SATA style to the older PATA style and swapped hard drives. That move fixed the situation for me.

---

### Post by mikeprosceo on 2010-03-27
This is actually an HP Pavilion laptop.  Yes, it was working fine for quite a while.  I noticed it around the time I had a new keyboard put into the laptop and then installed virus software (clamav etc.)  The computer seems to run slower and takes forever to open firefox and other things.  That is actually why I did a virus scan and put the virus software on the computer.  I was going to try to take the software off but I can't get to it.  Any Ideas? - Thanks - Mike

---

