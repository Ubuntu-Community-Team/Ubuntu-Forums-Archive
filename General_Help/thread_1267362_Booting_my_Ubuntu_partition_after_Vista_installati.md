---
title: "Booting my Ubuntu partition after Vista installation"
date: 2009-09-15
forum: General Help
---

### Post by balloonatic on 2009-09-15
OK so my Windows 7 partition decided to break so I decided to just bear it and install a Vista partition for gaming and Windows-only programs I need for university.

I wanted to keep the Vista partition small so I could keep loads of space on my Ubuntu partition (my default OS) so I only wanted about 20gb for Vista (it was currently about 60gb). So I used my System Rescue disk to run GParted to change the size of the Windows partition. 

Anyway, to cut this short, 20gb was not enough for installations so I went back to GParted and set it to resize the partitions again and went out. Came back hours later to find that it had randomly moved the partitions around and told me that both my Windows and Ubuntu partitions were empty. I cried. 

I then restarted and Vista booted up fine :confused: so I went back to GParted and it said my Windows partition was no longer empty. My Ubuntu partition remained empty according to it.

So I've assumed that the reason Windows appeared empty was that it had not been booted since partitions, and this is the same reason that Ubuntu appears empty. This is what I hope, because I have a horrible feeling that Ubuntu has been formatted.

In short: How can I boot Ubuntu from my Linux System Rescue CD/Ubuntu live CD? I've tried a couple of things and failed. My partition table is attached. My Ubuntu partition is sda5.

Please help me.

---

### Post by LowSky on 2009-09-15
boot into the ubuntu live cd and try to mount the drives.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ram2500 on 2009-09-15
**Do you have any files that you have lost?**

While you can install Ubuntu or most Linux distros on a machine with pre-existing Windows from a CD (I have done this before), it might be in the best interests of the faint-hearted to use Wubi. I did try this for a while, and it does work well. You can either make a partition from within Windows (Vista or 7) by going to Storage Management/Disk Management (something as such) and install Ubuntu in its own partition, or you can opt just to leave partitioning alone and just have Ubuntu in a folder. The real-time partitioning *usually* is harmless and will not let you make partitions if data or the integrity of Windows is in jeopardy. Both are good options, and both will present you with the Windows Boot Manager, presenting you with the option to boot either to Windows or Linux. 

I don't imagine that the boot CD can help you in this department, as the Windows partition had been messed with. Can you boot to Windows? We'll need to fix Windows first.

If you have files that are in jeopardy, I'd recommend placing the drive in another machine that either 1) runs Linux itself or 2) runs Windows but can access ext3 filesystems (you can download this utility from Sourceforge, among others).  I would copy those files over before you do anything else. Since you said that the partitions were empty, I am doubtful files would still be there, but in the case of urgency, it's worth a try.

---

### Post by balloonatic on 2009-09-15
I have followed the instructions up to:



```
mount /dev/sda2 /media/root
```



but I get the error:



```
mount: you must specify the filesystem type
```

I've tried adding a prefix of ext2, ext3 and ext4 to no avail.

---

### Post by Soley on 2009-09-15
> **balloonatic said:**
> I have followed the instructions up to:



```
mount /dev/sda2 /media/root
```



but I get the error:



```
mount: you must specify the filesystem type
```

I've tried adding a prefix of ext2, ext3 and ext4 to no avail.

Instead of ```
mount /dev/sda2 /media/root
```

try

```
mount /dev/sda5 /media/root
```

Since sda5 is where your ubuntu partition is.

---

### Post by balloonatic on 2009-09-15
The Vista partition boots fine, its just getting to my ubuntu partitions from a live cd. I study Computer Forensics at uni so if I have to give up and reinstall ubuntu I can easily recover most of my files, but I'd really rather avoid a format if I can.

---

### Post by balloonatic on 2009-09-15
> **Soley said:**
> Instead of ```
mount /dev/sda2 /media/root
```

try

```
mount /dev/sda5 /media/root
```

Since sda5 is where your ubuntu partition is.

Yeah, sorry I copy and pasted from the walkthrough, I did put sda5.

---

### Post by balloonatic on 2009-09-16
Still no luck, I've tried the UNetbootin-superdisk thing on that how-to through windows, no linux option at boot still. I really hope I'm not going to have to format :(

---

