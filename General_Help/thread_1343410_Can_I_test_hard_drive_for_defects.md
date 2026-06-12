---
title: "Can I test hard drive for defects?"
date: 2009-12-01
forum: General Help
---

### Post by mtate5000 on 2009-12-01
Does anybody know if i can test an internal hard drive using a live disk? I have jaunty on disk, can burn karmic if need be? This particular hd has been wiped clean, so theres no os on it. Im having trouble installing anything on it. Not sure if due to hd error or cd drive needs cleaning or both. Can't seem to get it to boot from a usb either (ive change every possible value in bios but wont boot). I can get the live disk to work some times but cant install on this older box. Dont know any of the hardware particulars at the moment. Any suggestions?

---

### Post by fooman on 2009-12-01
yeah,  you want to run fsck from the live cd...see here for a good explanation from bodhi.zazen:

[http://ubuntuforums.org/showthread.php?t=550491](http://ubuntuforums.org/showthread.php?t=550491)

---

### Post by whoop on 2009-12-01
fsck doesn't check the health of a hard disk, it checks the health of a filesystem.
To check the health of a hard disk you could use something like smartmontools...

Not being able to boot a livecd/usb would tend me to look in another direction than a broken hard disk, though.

---

### Post by shazbut on 2009-12-01
Best way is to use the hard disk manufacturer's provided tool.  They usually come in some bootable form, and provide a more reliable result than a general purpose test.

---

### Post by whoop on 2009-12-01
> **shazbut said:**
> Best way is to use the hard disk manufacturer's provided tool.  They usually come in some bootable form, and provide a more reliable result than a general purpose test.

running something like:
```

sudo smartctl -t long /dev/sda

```
would yield comparable results to any manufacturers tool, as long as it supports smart, wouldn't it?
This because the smart feature is in fact incorporated in the manufacturers hardware itself.

---

### Post by mtate5000 on 2009-12-01
i can boot jaunty from disk most of the time. it gets 60% through install then freezes. im sure the cd drive needs cleaning, that may be why it wont install. why it wont boot from usb is beyond me, my choices in bios are usb(fdd) , usb(zip), usb(cd-rom). i have linux mint on flash drive and karmic a wd passport. ive tried all usb options.

---

### Post by NFblaze on 2009-12-01
I believe the UBCD (Ultimate Boot CD) has quite a lot of tools for testing hard disks. Also, it can be run from LiveCD.

---

### Post by whoop on 2009-12-01
> **mtate5000 said:**
> i can boot jaunty from disk most of the time. it gets 60% through install then freezes. im sure the cd drive needs cleaning, that may be why it wont install. why it wont boot from usb is beyond me, my choices in bios are usb(fdd) , usb(zip), usb(cd-rom). i have linux mint on flash drive and karmic a wd passport. ive tried all usb options.

There is a test cd feature on the livecd, you can select it before booting (on the screen where you select: "Try ubuntu without installing" etc.)...

I never tried but I think you could run smartctl from the livecd, checking a drive can take a long time though (maybe run a short test first)...

---

### Post by shazbut on 2009-12-01
> **whoop said:**
> running something like:
```

sudo smartctl -t long /dev/sda

```
would yield comparable results to any manufacturers tool, as long as it supports smart, wouldn't it?
This because the smart feature is in fact incorporated in the manufacturers hardware itself.

Maybe. I was thinking more along the lines of a full sector scan and reallocate where necessary.  I've seen the western digital tool (used to be dlgdiag, dunno what they use now) revive supposedly dead drives, or find problems where other tools missed them.

---

