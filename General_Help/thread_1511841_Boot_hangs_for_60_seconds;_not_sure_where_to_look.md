---
title: "Boot hangs for 60 seconds; not sure where to look?"
date: 2010-06-17
forum: General Help
---

### Post by snurfle on 2010-06-17
I am looking to speed up my boot time; it is currently around the 2-2.5 minute mark from Grub to desktop (including about 15 seconds at the login screen while I type my password).

I have forced ureadahead to reprofile, and have rebooted a few times until the boot time is fairly stable/consistent.

No xorg errors and only one warning 
((WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.)

However, dmesg reports the following:

```
...
[    1.121369] Freeing unused kernel memory: 656k freed
[    1.121926] Write protecting the kernel text: 4676k
[    1.121977] Write protecting the kernel read-only data: 1840k
[    1.146159] udev: starting version 151
[    1.490301] b44 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.548311] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.548736] b44.c:v2.0
[    1.569028] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:92:bd:33
[    1.658534] kjournald starting.  Commit interval 5 seconds
[    1.658550] EXT3-fs: mounted filesystem with ordered data mode.
[   72.265461] udev: starting version 151
[   72.341338] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k 
[   72.438874] lp: driver loaded but no devices found
[   72.624871] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   72.667541] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
...
```

It consistently has that 'lag' in there of 60-70 seconds, and I do not have a clue on where to begin finding out what is going on.

I would appreciate anyone showing me where to start looking for clues to this.


Machine:
Dell Inspiron B120
Ubuntu 10.04 (lucid)
Gnome 2.30.0 (Ubuntu 2010-03-31)
Kernel 2.6.32-22-generic 
CPU Intel(R) Celeron(R) M processor 1.40GHz
2GB Ram
120GB HDD  WDCWD1200BEVE-0


Thanks!

---

### Post by arrange on 2010-06-17
You can get more info from a *bootchart*:
[http://www.webupd8.org/2009/04/ubuntu-boot-chart-make-graph-with-your.html](http://www.webupd8.org/2009/04/ubuntu-boot-chart-make-graph-with-your.html)

I would also try disabling *ureadahead*: for a test move the *ureadahead* files out of the */etc/init* directory (if that doesn't help, move them back - I don't know of any other way of disabling *ureadahead* temporarily).

---

### Post by snurfle on 2010-06-17
Thanks for the suggestion.

OK... here goes...

With ureadahead running and after a few full boot cycles, I have the aforementioned ~60 second 'lag', and from Grub to Desktop is 2-2.5 minutes.

So...

I installed bootchart, and rebooted twice (just to make sure I had a good baseline.)
Bootchart clearly showed that ureadahead was the culprit responsible for the 60 sec lag.

I then deleted the ureadahead pack file, and renamed the ureadahead.conf files to 123.conf.disabled and then rebooted twice just to be certain...
dmesg now reports:
```
...
[    1.577842] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.578095] b44.c:v2.0
[    1.597015] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:92:bd:33
[    1.655425] kjournald starting.  Commit interval 5 seconds
[    1.655441] EXT3-fs: mounted filesystem with ordered data mode.
[    4.269292] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k 
[    5.182148] EXT3 FS on sda1, internal journal
[    5.475540] udev: starting version 151
[    6.478771] cfg80211: Calling CRDA to update world regulatory domain
...	
```

Which has all the appearance of a "ta-daah" moment.

However, 
It is now taking a full 3 minutes before I get to the desktop, which I see as a step backwards.

My only conclusion is this:
ureadahead takes 30-45 seconds off my boot time, and is doing it's thing immediately after the filesystem is mounted.
Based on a post from the developer [here]("http://ubuntuforums.org/showthread.php?t=1434502"), it is doing what is supposed to do... knocking time off of the boot process.

There is nothing obvious on the bootchart which shows an obvious cause for such a long delay, although I may not know what I am looking at/for.
The png file is 1.1MB, and the tar file is 10.2MB, so I don't really have the option to post them here.
Is there something specific I should look for to find what is taking so long to boot up?

---

### Post by arrange on 2010-06-17
So *ureadahead* is not to blame then...
Post the image on senduit.com, *imageshack* or wherever else.

---

### Post by philinux on 2010-06-17
Could be the floppy problem.

See the General Help forum Sticky.

---

### Post by snurfle on 2010-06-17
post the picture elsewhere... geez, I'm a bonehead!

[it's here...]("http://www.flickr.com/photos/cluelessinohio/4709850270/")

---

### Post by arrange on 2010-06-17
I'd check the HDD (SMART data), for example using the *Palimpsest Disk Utility*.

---

### Post by snurfle on 2010-06-17
> **philinux said:**
> Could be the floppy problem.

See the General Help forum Sticky.

Checked the BIOS, no mention of a floppy anywhere at all.


> I'd check the HDD (SMART data), for example using the Palimpsest Disk Utility.

Hmmm...  Not sure how to interpret all this...
Self-Assesment : Passed
Self-Tests: Completed OK
Bad Sectors: None
Overall Assessment: Disk is healthy

Read Error Rate
Assessment: Good
Normalized: 200
Worst:      200
Threshold:  51
Value:      11

None of the other attributes (involved in errors) have other than a Zero value.

But I don't know quite what to make of this.  Does this mean that there have been 11 read errors?  I'm not quite sure what any of these values actually mean...

---

### Post by snurfle on 2010-06-22
I hate to <bump> this one, but I am at a loss.
I can't find any solid info about the meaning of the SMART data on a WDC drive.
But the 60 second delay at boot is still there with ureadahead enabled (and 2.5 minutes to a desktop); without it there is no single item causing the lag, but my boot time is still at about 3 minutes.

---

### Post by arrange on 2010-06-22
The *Read Error* does not explain the problem (I think they are quite common at this rate).

Can you try booting into *Recovery Mode*? Do you see the same lag? If so, disable *ureadahead* and provide the *syslog* again.

---

### Post by JohnnyB98604 on 2010-06-22
I had an issue with my BIOS settings around the SATA drive.  It was set  to AHCI (or something like that) and it needed to be switched to "Compatibility".  My boot-times went from several minutes to 60 seconds or less.

This was on a Toshiba netbook...not that it matters.

---

### Post by snurfle on 2010-06-23
OK...
I disabled AWN from starting automatically; it appeared to be adding about 10 seconds at startup, and I removed bootchart as well... During all the rebooting, my system ran a fsck and it took bootchart nearly 3 minutes to generate the .png file after I got to the desktop.

There is nothing in the BIOS relating to the HDD other than "Acoustic mode"; I have it set to "performance" rather than "quiet".  (Good suggestion, though.  Thanks, JohnnyB9604!

Recovery mode didn't go any faster than normal.

So after a fairly large update last night (CUPS had a large update); I did 2 cold boots this morning just to make sure everything is stable...
AWN turned off, OpenOffice quick starter turned off, ureadahead disabled, and no bootchart.  Still at 2:15 to 2:30 from grub to desktop.

Syslog is attached.

---

### Post by arrange on 2010-06-23
It looks like it is waiting for internet connection... How do you connect?

---

### Post by snurfle on 2010-06-23
> **arrange said:**
> It looks like it is waiting for internet connection... How do you connect?

Not to sound like a noob, but where do you see this?  I really did not expect that to be my issue!
I am connecting wirelessly with a D-Link DWA-643 Xtreme N ExpressCard using ndiswrapper, to my linksys router running ddwrt.

---

### Post by arrange on 2010-06-23
No, it's just a guess, I can see some messages concerning this, but nothing in particular... But you can test it with wired connection if it's possible.

I'd also try booting without *plymouth* and (to rule out a HDD issue) booting into a LiveCD (which of course will be slower, but you still should be able to see if you have a similar lag or not).

---

### Post by snurfle on 2010-07-01
Wired connection made no difference...
I cannot find any good instructions on how to boot without plymouth... suggestions?

I installed Python 2.6.5 the other day to try a few things that I can't do in GAMBAS, and I think I hosed my system... no icons, most of the apps in AWN don't launch, nautilus won't launch... I think a little lag in my bootup just became the least of my issues.
I will try to get the Python issue resolved, but it looks pretty bleak at this point.  
Assuming I can get it fixed, then I will come back to the 'lag' issue, but I think I am getting close to the wipe and reinstall" point.   GAAAAAAA!!!

---

### Post by snurfle on 2010-07-02
Oh, geez.
Bad to worse.

There was a kernel update yesterday, which I installed.

Now, at startup and shutdown I have a new splash screen...
A full screen image of a group of blue concentric circles, and text underneath that reads "ubuntu studio", half of the first "u" is white, the rest of the "u" and the balance of the letters are black.

A quick google of "ubuntu studio" returns results that lead me to believe something... "else"... was installed with the kernel update.

So now my system is like this:

I still have a 3-minute boot time.
I am not running ureadahead.
I am running a direct wired connection to the internet rather than wireless.
I am no longer running AWN or OpenOffice Quick starter.
fsck and palimpsest do not report any HDD issues.
I cannot find any source that explains how to disable plymouth without borking most of the system in the process.
And now, I am apparently running "ubuntu studio", although I cannot find anything other than the splash screens that confirm this.

sysinfo returns the following:
Release: Ubuntu 10.04 (lucid)
Gnome : 2.30.0 (Ubuntu 2010-03-31)
Kernel: 2.6.32-23-generic (#37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010)

Any sort of direction at this point would be greatly appreciated.

[ATTACH]162166[/ATTACH]

---

### Post by snurfle on 2010-07-03
I've done a lot of reading up on Plymouth; I can't find any real concrete information about it other than:
1.  Lots of people don't like it.
2.  It cannot be removed.
3.  It seems to be mentioned in conjunction with other 'boot delay' issues, but those mostly seem to be related to graphic driver issues.

I can NOT however, find any reports of the 2.6.32-23 update bringing along 'Ubuntu Studio' with it.

*confused and frustrated*

---

