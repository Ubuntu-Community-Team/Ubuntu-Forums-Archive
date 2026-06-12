---
title: "ubuntu won't start - stuck at loading screen"
date: 2011-01-05
forum: General Help
---

### Post by wiseguy12851 on 2011-01-05
I simply installed 5 or 6 various packages and shutdown the laptop, later I opened it and turned it on GRUB came up as usual showing the usual options, I selected the option I always pick and Ubuntu came up as usual with the progress bar of 5 or 6 dots that show the typical progress bar but it stays like this forever. I tested it for up to 3 hours it didn't budge.

I tried selecting the recovery option from the GRUB menu and it appears to load normally with a bunch of console output but then halts with the last message displaying:

```
cloud-init start-local running Wed, 05 Jan 2011 20:43:44 -0600. up 14.26 seconds
no instance data found in start local
init: cloud-init-local main process (357) terminated with status 1
```

But before the message there was a lot of warnings that appeared to trail off as there were so many, here is an example of one of them as they all appear to be the same just different rule numbers, this is also the last one before the error:

```
udevd[353]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/99-sbig.rules:59
```

---

### Post by mmsmc on 2011-01-05
do you remmember the packages you installed?

---

### Post by wiseguy12851 on 2011-01-05
It was like 5 Meta Packages and a few other non-meta packages, I was going through the system administration category when I was installing them from synaptic, I have been intensely installing packages for the last 5 days as this is a new installation when this problem came up.

I have no experience with fixing boot problems so I don't know how to go about this.

---

### Post by Krytarik on 2011-01-05
I followed a thread about a similar problem earlier today:
[http://ubuntuforums.org/showthread.php?p=10320951#post10320951](http://ubuntuforums.org/showthread.php?p=10320951#post10320951)

After "chrooting" into your system, try (like in the other thread):
sudo dpkg --configure -a

If that doesn't help try removing the most recently installed packages:
```
sudo apt-get remove --purge PACKAGES
```

To check what packages those are, look in "/var/log/apt/history.log".

---

### Post by wiseguy12851 on 2011-01-05
Turns out it around 19 packages that was installed, is there a way I can figure out what packages might be causing the problem or do I have to uninstall those packages - see if it boots correctly - if it does then gradually add the packages back one at a time rebooting in between to find the ones not to add?

---

### Post by Krytarik on 2011-01-06
> **wiseguy12851 said:**
> Turns out it around 19 packages that was installed, is there a way I can figure out what packages might be causing the problem or do I have to uninstall those packages - see if it boots correctly - if it does then gradually add the packages back one at a time rebooting in between to find the ones not to add?
Unfortunately the latter. Then the first mentioned command didn't solve it?

EDIT: You could also check first "/var/log/messages" for the last messages that have been logged before it froze, maybe they include a valueable error message.

---

### Post by wiseguy12851 on 2011-01-06
I'm sure that will work, but since this is a completely new installation there is no personal files saved anywhere so I'll just reformat and be a little more careful with what I install. 

Thanks for your help, if this does happen again I know how to boot in like that

---

### Post by Krytarik on 2011-01-06
Did you notice my edit of my previous post? Maybe it's worth checking before re-installing.

---

### Post by wiseguy12851 on 2011-01-06
I followed your new edit, here's the error message

EXT4-fs (sda2): remounted. Opts: errors=remount-ro,commit=600
EXT4-fs (sda2): remounted. Opts: errors=remount-ro,commit=0
ata1: hard resetting link
ata1: applying SB600 PMP SRST workaround and retrying
ata1: SATA link up to 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: configured for UDMA/133
ata1: EH complete

---

### Post by Krytarik on 2011-01-06
> **wiseguy12851 said:**
> I followed your new edit, here's the error message

EXT4-fs (sda2): remounted. Opts: errors=remount-ro,commit=600
EXT4-fs (sda2): remounted. Opts: errors=remount-ro,commit=0
ata1: hard resetting link
ata1: applying SB600 PMP SRST workaround and retrying
ata1: SATA link up to 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: configured for UDMA/133
ata1: EH complete
There is no real error message, the first two lines just state the mount options at failsafe boot, the rest doesn't contain a serious message either.

Then go ahead, re-install.;-)
Or choose the other way.

---

