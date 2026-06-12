---
title: "Unable to mount ... CDROM"
date: 2010-01-20
forum: General Help
---

### Post by pingu1 on 2010-01-20
I am unable to mount a cd-rom. It shows an icon on my desktop when I insert DVD's, and I am able to read DVD's in VLC, but I cannot read any other cds.
Before when I put a cd in, the icon automatically showed up, but not anymore.
I have been screwing around a bit in Ubuntu, and added/removed some peckages which probably caused this.

My fstab-file - which I understand probably will be a good diagnose of my problem reads:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b48b2b8f-fdb2-4fa1-9748-1ec84671f8f3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3e6f2415-b9cd-45a7-bcce-1d2fdb93313b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by pingu1 on 2010-01-20
fdisk output:
> sudo fdisk -l
[sudo] password for home: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e6f710e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris
home@home-laptop:/dev$ 


---

### Post by pingu1 on 2010-01-21
Is there anybody who can tell me where the problem is?

---

### Post by jamesisin on 2010-01-21
Try mounting the drive manually.  Go into /dev and use the mount command:

sudo mount /dev/[yourCDdrive]

You'll have to sort out which device is your CD drive, of course.  If you get errors, post them here.

---

### Post by Grenage on 2010-01-21
I haven't seen this before, but recall someone having a similar problem.  Just for fun, swap *udf* and *iso9660* around:

```
/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0
```

Reboot and see if there is any difference.  If not, put them back as they were.

---

### Post by pingu1 on 2010-01-21
So am I interpreting you correctly then, that there probably is nothing wrong with mtab or fstab? The problem is me? 

I am currently at work, but I will try later today,,,

---

### Post by pingu1 on 2010-01-21
Anybody got any clue as to why this happens? I have only installed som plugins/programs, and, well, tried to make the computer "mine" - as in customizing menus and stuff...

When these things are in perfect order after the installation, there should not be made any changes to these files - UNLESS you _really_ want to. Maybe the system should ask you, when you do something which affects these thing, _if_ you really want to make these changes?

I love Ubuntu, but I've already re-installed 2 times, in about 1 month!

---

### Post by Grenage on 2010-01-21
> So am I interpreting you correctly then, that there probably is nothing wrong with mtab or fstab? The problem is me?

No, it doesn't sound like it's anything you have done.  The only times I've heard of people being able to read either CDs or DVDs were when there was an issue with the drive itself.

---

### Post by pingu1 on 2010-01-21
If the issue is the drive itself - is the probable solution what you wanted me to test (ref. over) ? 

I don't understand how a drive that works just fine, all of a sudden can have an "issue" :(

I hope I don't have to re-install again... I was so happy, everrything worked just fine!!

---

### Post by Grenage on 2010-01-21
Drives can just fail, any computer equipment can; a reinstall won't help if that is the case.  Do you have any other machines that you can test the drive in, or another drive you can test in your machine?

---

### Post by pingu1 on 2010-01-21
It's a laptop. The cd-rom in question is the internal one....

---

### Post by Grenage on 2010-01-21
I see.  In that case, try booting the laptop with the Ubuntu live CD.  If it works, you'll know that the drive is fine.

---

### Post by pingu1 on 2010-01-21
Okay, I see. I will try. Thanks.

---

### Post by jamesisin on 2010-01-21
Ubuntu has software which can test the drive performance.  See this post:

[http://ubuntuforums.org/showpost.php?p=8700168&postcount=9](http://ubuntuforums.org/showpost.php?p=8700168&postcount=9)

---

### Post by pingu1 on 2010-01-21
Hi. I tried booting the Ubuntu cd - didn't work.
It seems it detected the cd on the boot, but still I finally ended up in normal booting with Ubuntu from the drive.

I dont understand anything....!

---

### Post by pingu1 on 2010-01-21
> home@home-laptop:~$ dmesg | tail
[  143.580760] UDF-fs: No anchor found
[  143.580763] UDF-fs: No partition found (1)
[  143.604477] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[  143.604490] sr: Sense Key : Hardware Error [current] 
[  143.604495] sr: ASC=0x9 <<vendor>> ASCQ=0x90
[  143.613189] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[  143.613199] sr: Sense Key : Hardware Error [current] 
[  143.613203] sr: ASC=0x9 <<vendor>> ASCQ=0x90
[  143.623024] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=32
[  154.860825] ACPI: EC: non-query interrupt received, switching to interrupt mode
home@home-laptop:~$ 
  

I don't understand...

---

### Post by pingu1 on 2010-01-21
Another error-message:

> home@home-laptop:~$ sudo mount -t iso9660 -o ro /dev/cdrom /cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by pingu1 on 2010-01-21
Also - when i enter the system - administration - disk utility, it says on the cdrom:
CD/DVD Drive
1.1 GB / 1024 MIB /1,073,741,312 bytes
Unrecognised
SMART is not available
/dev/sr0

---

### Post by jamesisin on 2010-01-21
Did you run the test I linked to above?

---

### Post by Grenage on 2010-01-21
Sounds like a bad drive to me.

---

### Post by pingu1 on 2010-01-22
You're probably right. It sees the cd, apparantly, when I try to boot it, because the cdromlight flashes, but I don't hear the normal sound from the cd spinning. Is it easy to get a new cdrom and replace it myself? (I still haven't tested enough of course). If that is my only option, anybody know?
The computer is a few years old now (probably 5-6 yrs old) - is it worth it?

---

### Post by Grenage on 2010-01-22
Bah, 5-6 years is nothing, and drives are cheap!  It's very easy to replace, just take the side off the case and take a look at the cable connected to it.  It will be IDE (wide ribbon cable) or SATA (much smaller), just make sure you get the same kind.

---

### Post by jamesisin on 2010-01-22
Grenage - It's a laptop so the drive could end up being quite expensive and won't be connected with any cables.

---

### Post by Grenage on 2010-01-22
Good spot, I'd forgotten that it was a laptop.  In that case he'll just have to look around for a replacement, and decide if it's cost effective.

---

### Post by pingu1 on 2010-01-22
I just checked something: I had no disc in the drive - then went into System Administration "Disk Utility"  - and then put a blank cd in - it detects the cd. A new "tab" opened up after a few seconds. Maybe the cdrom isn't bad after all? Anyway - if it isn't I still don't know what to do.... :(

---

### Post by jamesisin on 2010-01-22
My experience of dying/dead CD drives is pretty annoying.  They usually don't fail entirely all of a sudden.  Some aspect fails and you're there going "did this burn fail when I did it two weeks ago?" or "is this iso I'm trying to burn today no good?".  Later on you find that it's any burned disc or any iso (or any [fill in your pattern here].

See if you can borrow a USB CD drive and test using that.  This will tell you if the OS is capable (and it should be) of reading burnt discs.  If you find that it's still the same set of discs which can't be read, you know it's not the drive.  If they set of discs changes, you can be pretty sure it's the drive.

---

### Post by pingu1 on 2010-01-22
I tried your test:
> home@home-laptop:~$ ddrescue /dev/cdrom /dev/null ddrescue.log


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:   1073 MB,  current rate:        0 B/s
   ipos:   672415 kB,   errors:       1,    average rate:        0 B/s
   opos:   672415 kB,     time from last successful read:      46 s
Finished                   
home@home-laptop:~$ 


---

### Post by jamesisin on 2010-01-22
I'm not sure about what the error output means.  I asked someone else to take a look.

I get similar output from a burned disc (very old) and a store bought music CD.

Here is the store bought music CD (8.10 machine):

```
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:    410 MB,  current rate:        0 B/s
rescued:         0 B,  errsize:    426 MB,  current rate:        0 B/s
   ipos:   426180 kB,   errors:    6504,    average rate:        0 B/s
   opos:   426180 kBing logfile ddrescue.log for writing: Permission denied
```

---

### Post by pingu1 on 2010-01-22
yes, that is also my interpretation of the link previously posted...

---

### Post by jamesisin on 2010-01-22
Same CD, different machine (9.10):

```
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:    588 MB,  current rate:        0 B/s
   ipos:   269562 kB,   errors:       1,    average rate:        0 B/s
   opos:   269562 kB,     time from last successful read:    35.4 m
Finished
```

---

### Post by pingu1 on 2010-01-23
Okay.... so anybody know how we ought to interpret these results? Including mine?
I think I have confirmed a faulty cdrom - because today i brought my laptop with me to another location, startet it up, and all of a sudden - the cdrom worked fine!! It read cd's, and I tried burning a cd - although the cd turned out to end in a errormessage, I confirmed that it had burned all the files over to the cd - although I could not open the files afterwards - probably a fault in the "closing"-part of the burning process.
I got to read a cd,  tried to burn a cd - with partial success - and then - AGAIN - the cdrom failed.
It disappears, and is no longer availiable to me. Starts shining its light constantly and so on....

I think I'm just gonna pretend that the computer has no cdrom from now on, which sucks, but I don't think I want to spend money on a new one - as I actually spoke to the previous owner of the computer, and he had similar problems, actually having had to change cdrom earlier, so the cdrom I have in the computer is the second one....

---

### Post by flabdablet on 2010-01-27
**Press Ctrl-C to interrupt** means what it says; you can interrupt a ddrescue run at any time, and ddrescue will note where it's up to in its log file and then quit. If you then do another ddrescue run specifying the same log file, it will pick up where the previous run left off.

[b]Initial status (read from logfile)
rescued: 0 B, errsize: 0 B, errors: 0[/b]

Before the start of this run, ddrescue had read no bytes, and encountered no read errors in no ranges of contiguous blocks.

[b]Current status
rescued: 0 B, errsize: 1073 MB, current rate: 0 B/s[/b]

During this run, ddrescue managed no successful data reads, but encountered errors during 1073MB of attempted reads, and is currently transferring data at zero speed.

**ipos: 672415 kB, errors: 1, average rate: 0 B/s**

ddrescue is currently attempting to read at a point 672415 kB from the start of the input file (in this case, the disk drive), has encountered one range of contiguous blocks containing errors, and is achieving a data transfer speed of zero.

**opos: 672415 kB, time from last successful read: 46 s**

ddrescue is currently positioned at 672415 kB from the start of the output file (in this case, the bit bucket) and this is where it will begin to write data it manages to read from the input, if any.

Something else you could look at is the contents of ddrescue.log. The format is pretty simple: each line has a byte offset from the start of the input file, a number of bytes, and a one-character status code:

+: This byte range was read without errors.
-: This byte range could not be read.
/: This byte range contains errors and should be re-scanned using a smaller read size.
?: No reads have yet been attempted in this byte range.

What I think the ddrescue output is trying to tell you in this case is that (a) it can't read any data at all from your drive and (b) the drive reports the available size of the inserted medium as 1073 MB, which strikes me as strange.

You won't get sensible results from ddrescue by attempting to use it with audio CD's, which are not traditional block-structured media (their data blocks contain no positioning information) and need to be read in special ways. Here are the [gory details]("http://www.cdrfaq.org/faq02.html#S2-11") if you're interested in that kind of thing.

tl;dr: your drive or your discs are busted.

---

### Post by pingu1 on 2010-01-28
For some strange reason - my cdrom now functions fine! I burned a cd last night, XviD, slammed it into my dvdplayer (supports DivX), and it worked fine. 2 episodes of mythbusters was very good.
Good quality, no errors... I'm clueless as to why it all of a sudden works, but it does.

Hope it stays this way.... I just suddenly got the cdrom icon on my desktop, and tried.... Jippi.

-Only 3 things are certain: taxes, gravity and death.

---

### Post by pingu1 on 2010-02-07
Just wanted to let you guys know that my computer now, finally, also recognises the brand and type of cdrom I have. Earlier, even though it worked, it did not know what kind of cdrom my laptop had. Now it shows: System -> Administration -> Disk Utility: CD/DVD drive, MATSHITA DVD-RAM UJ-83OS.

Maybe it got fixed during a system-update, without telling me?

---

