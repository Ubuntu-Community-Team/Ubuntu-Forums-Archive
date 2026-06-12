---
title: "Issue burning 11.04 iso suspect hardware problem"
date: 2011-05-29
forum: General Help
---

### Post by Nervouswreck on 2011-05-29
I'm running Karmic and finally decided to upgrade. When I inserted my blank disc for 11.04 Brasero shows my blank disc as "Blank CD --drive name here -- 17.5 MB free space"

I proceed to burn anyway figuring that it's some kind of read error and I have nothing to lose by attempting the write. (I did in fact lose 3 discs, about 50 cents). 

Disc writes fine but hangs for about 5 minutes during the finalizing stage and then stops with an error.

Is there any hope of this being a software problem that I can fix without replacing the drive? (My laptop is just out of the extended warranty)

Thanks in advance.

---

### Post by linuxinstalledfromhdd on 2011-05-29
If you scan the last few days of this forum, one thing will become aberrantly clear. 11.04 has bugs.  Use 10.10 32-bit and you can't go wrong.

---

### Post by Nervouswreck on 2011-05-29
Thanks, that tip will save me some time and irritation.

PS Aberrantly clear? Do you mean that something being clear is an aberration or that it's an aberration for new releases to have bugs? ;)

---

### Post by linuxinstalledfromhdd on 2011-05-29
My spell checker made a mistake. ;)

---

### Post by TeoBigusGeekus on 2011-05-29
Try burning it from command line
```
wodim -v dev=/dev/scd0 /path/image.iso
```
Replace scd0 with whatever applicable (sr0, cd, cdrw, dvd, etc.)

---

### Post by Nervouswreck on 2011-05-30
TeoBiggusGeekus: Thanks. I tried using wodim but it didn't work. Can you help me understand the log, please?

```

wodim: No write mode specified. //got this. The manpage said it would pick a default
wodim: Asuming -tao mode. //fine
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/media/cdrom0' //Is this memory access? What operation?
devname: '/media/cdrom0'
scsibus: -2 target: -2 lun: -2
wodim: Is a directory. //Of course it's a directory! Both arguments are paths.
Cannot open SCSI driver! //SCSI?! I didn't think I was using a SCSI drive in my laptop?
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```

---

### Post by TeoBigusGeekus on 2011-06-01
What was the exact command you used?
You didn't use /media/cdrom, did you?
That's why it complains about it being a folder - you have to use a device, /dev/cd, /dev/sr0, etc.

---

### Post by dFlyer on 2011-06-01
> **linuxinstalledfromhdd said:**
> If you scan the last few days of this forum, one thing will become aberrantly clear. 11.04 has bugs.  Use 10.10 32-bit and you can't go wrong.

If it's 9.10 burning the disk, I don't see how 11.04 bugs can be causing the burn problem if the md5sum is correct. I do agree 11.04 has bugs, but that should have nothing to do with 9.10 cd burning. I also believe a lot of 11.04 bugs have been fixed since it's release, and most of the problems are people pushing unity beyond it ability to function correctly with internal hacks. I say give unity time and it will be a good desktop. Just don't forget gnome is available with the 11.04 download as an option for a desktop.

---

### Post by Nervouswreck on 2011-06-02
Yeah, I realized that after I posted. Still didn't work. In the end I burned the cd on my Mac OSX desktop. Now I'm having a different issue, though I think I'll have to start a new thread for it. I'm booting from the cd and it hangs for a while then I get a shell from something called "ubuntu busybox" which I guess is the stripped down shell used for installation, and it says that it "can't find a live filesystem" which I'm assuming means the cd isn't mounting. What gives?

---

### Post by bazcor on 2011-06-02
I would suspect something is wrong with the PC. Does the CD pass it's file test on boot? I assume you have the correct 'bitness' for the pc.

Might be worth running the memory test program on the CD. Has the PC been working correctly for some time?

Maybe a couple of things to think about. Good luck .. Barry

---

