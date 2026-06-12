---
title: "Ubuntu Gparted / Windows Partition Problems"
date: 2010-10-22
forum: General Help
---

### Post by craig101 on 2010-10-22
Hello,

I have a dual booted Ubuntu / Windows Seven partition.

I noticed yesterday that on my Ubuntu I was unable to access the Windows part of my drive like I had previously been able to (and Windows still works fine) and today when I tried to run Gparted I got this error:

"Inhibit all polling failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

And well I have no clue how to fix the problem, and can't find any help.

I have also since yesterday had the problem that numerous times it loads into a command line and I have to use the startx command, and whenever I log in with the GUI I get a 'Power Management Not Responding' and have to wait about half a minute for it to close and then login proceeds as normal.

---

### Post by craig101 on 2010-10-23
I have just done f-disk and this looks wrong and i feel maybe the problem (but no idea how to fix it)

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       55702   447319040    7  HPFS/NTFS
/dev/sda3           55703       60801    40957717+   5  Extended
/dev/sda5           60201       60801     4827532+  82  Linux swap / Solaris
/dev/sda6           55703       60199    36122089+  83  Linux


---

### Post by coffeecat on 2010-10-23
I've seen the "partition does not end on cylinder boundary" message before and I don't believe this is a problem. It's the boundary between the  Windows 7  boot partition on sda1 and the C: "drive" on sda2.  If Windows is working OK I doubt whether it's worth worrying about.

I don't think being unable to access the Windows partition is anything to do with this. It sounds like just one part of an escalating problem which culminates with your login problem and the "Power Management Not Responding" message.

Googling that message brings up these two bug reports.

[https://bugs.launchpad.net/ubuntu/+bug/587986](https://bugs.launchpad.net/ubuntu/+bug/587986)

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862)

Is there anything in those relevant to you?

Apart from that I don't know what else to suggest, apart from googling the "Inhibit all polling failed" message.

What version of Ubuntu are you running? Is it up-to-date? Did these problems occur after a kernel upgrade? Have you tried booting into an older kernel?

---

### Post by Hippytaff on 2010-10-23
> 
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9730    78052353    5  Extended
/dev/sda5              13         256     1951744   82  Linux swap / Solaris
/dev/sda6             256        2079    14647296   83  Linux
/dev/sda7            2079        9730    61451264   83  Linux
My fdisk -l...works fine, maybe it is another issue causing the problem - though I don't have a windows partition

---

### Post by srs5694 on 2010-10-23
Try running CHKDSK in Windows on the disk in question (probably C:). If it reports errors, run it again, and repeat until it reports no errors. Then try it again in Linux.

---

