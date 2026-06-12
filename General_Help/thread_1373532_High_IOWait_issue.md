---
title: "High IOWait issue"
date: 2010-01-05
forum: General Help
---

### Post by misterPhyrePhox on 2010-01-05
Hello,

I've been having a problem in Ubuntu 9.10 recently where starting about 2 minutes after startup my computer slows down and becomes unresponsive. I believe the problem is associated with a high IOWait because I have the system monitor applet on my Gnome Panel and it displays 100% IOWait every time my system starts to slow down.

I have tried booting into other kernel version and the problem persists.

I don't really know what IOWait is or how to diagnose this problem further. I've looked around online and it seems like you have to find a specific process that is causing the IOWait, but I don't understand how to go about doing that.

Can anyone help me or relate their experiences with this issue?

Thanks in advance for your replies.

---

### Post by jonest1 on 2010-01-05
Try running the top command in the terminal.  If an application is using a lot of disk and is active, it will probably show up at the top of the list.

Also, you may try disabling certain items.  For example, turn off the compiz visual effects and see if that helps.

You may also have some hard disk problems, but it's better to check off other items first.

---

### Post by 3rdalbum on 2010-01-05
You could install iotop, to show you what is thrashing your I/O. My guess would be some sort of disk indexing program like Tracker.

---

### Post by dcstar on 2010-01-05
> **3rdalbum said:**
> You could install iotop, to show you what is thrashing your I/O. My guess would be some sort of disk indexing program like Tracker.

Or there are bad blocks somewhere on the drive causing multiple retries.

Turn on SMART in the BIOS and see if problems get reported.

---

### Post by misterPhyrePhox on 2010-01-06
> **dcstar said:**
> Or there are bad blocks somewhere on the drive causing multiple retries.

Turn on SMART in the BIOS and see if problems get reported.

I am currently running this "Hard disk drive diagnostic program" that I found in the BIOS. I'm not sure if that's S.M.A.R.T., but maybe it'll find something.

I tried running top and iotop and I can't see any specific process that's causing all the IOWait. Sorry if this is a newbie question, but I noticed that top only displays as many processes as can fit in the terminal window -- however, aren't they sorted by CPU usage (or IO usage in iotop), so if a process was acting up it should go to the top of the window and I'd see it right? I'll have to look again after this diagnostic program finishes.

Thank you all for your suggestions!

---

### Post by lavinog on 2010-01-06
You can also get iowaits with usb drives and cd/dvd disks too.
typing dmesg in a terminal might say something too.

---

### Post by misterPhyrePhox on 2010-01-06
Well this is interesting.

The hard drive diagnostic program has found an error. It says:
[INDENT]Error code 0000: Read verification failed[/INDENT]
This looks bad. My laptop is a Lenovo Thinkpad T61 by the way. I guess I'll google this.

---

### Post by misterPhyrePhox on 2010-01-06
> **misterPhyrePhox said:**
> Well this is interesting.

The hard drive diagnostic program has found an error. It says:
[INDENT]Error code 0000: Read verification failed[/INDENT]
This looks bad. My laptop is a Lenovo Thinkpad T61 by the way. I guess I'll google this.

I should mention also that I dual boot. I have a Microsoft Windows XP partition, and I can boot into XP and run programs fine; I haven't had any problems there.

Edit: I just found [this page]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63376") which, although its for the X60 series, suggests that this might just be a bug in the BIOS.

---

### Post by dcstar on 2010-01-06
> **misterPhyrePhox said:**
> I should mention also that I dual boot. I have a Microsoft Windows XP partition, and I can boot into XP and run programs fine; I haven't had any problems there.

If the possible bad block is on the part of the disk that Linux uses, then this would be a typical symptom.

There is a tool called badblocks which can scan your Linux partition for these things:

```
man badblocks 
```

---

### Post by misterPhyrePhox on 2010-01-06
I just booted into Ubuntu and there's a notification icon that says my disk has many bad sectors. It says I should back up all data and replace the disk. Is this my only option?

The specific attribute that has a warning is the Current Pending Sector Count. The description is:
[INDENT]Number of sectors waiting to be remapped. If the sector waiting to be remapped is subsequently written or read successfully, this value is decreased and the sector is not remapped. Read errors on the sector will not remap the sector. It will only be remapped on a failed write attempt.[/INDENT]

Under the "Value" column in Palimpsest it says:
[INDENT]Normalized: 100
Worst: 100
Threshold: 0
Value: 72 sectors[/INDENT]

---

### Post by dcstar on 2010-01-06
> **misterPhyrePhox said:**
> I just booted into Ubuntu and there's a notification icon that says my disk has many bad sectors. It says I should back up all data and replace the disk. Is this my only option?

The specific attribute that has a warning is the Current Pending Sector Count. The description is:
[INDENT]Number of sectors waiting to be remapped. If the sector waiting to be remapped is subsequently written or read successfully, this value is decreased and the sector is not remapped. Read errors on the sector will not remap the sector. It will only be remapped on a failed write attempt.[/INDENT]

Under the "Value" column in Palimpsest it says:
[INDENT]Normalized: 100
Worst: 100
Threshold: 0
Value: 72 sectors[/INDENT]
Boot off a live CD and run this (find your /dev/ name first):
```
e2fsck -c -c -k /dev/whatever
```
This will cause a non-destructive write on the entire Linux partition which should trigger the remapping.

---

