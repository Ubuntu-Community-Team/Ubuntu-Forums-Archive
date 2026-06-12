---
title: "Dying Ext3-fs partition"
date: 2009-09-28
forum: General Help
---

### Post by Mikael P. on 2009-09-28
Hello forum,
yesterday I asked about my /home being read only. It seemed like the worst predictions were true. It is dying.
So I would like to salvage what I can and turn to you dear forum for assistance.

This is what I got when booting into recovery mode:
-----------------
/dev/sda5 Unexpected inconsistency run fsck manually
(Without -a or -p options)

Fsck died with exit status 4

File system check failed
-----------------
Before this when restarting the system there were plenty of DRDY ERR and ATA Bus error messages.

So my question is, can I do anything in recovery mode to milk some bits out of the system? Or should I place my bets on data recovery tools by using Windows?
Running a trial of DiskInternals recovery tool I could find some files but it was a pretty mess so I can't imagine getting many files out of that.
Or is there some other tool out there that does a better job?

Thanks for your time!

---

### Post by falconindy on 2009-09-28
Unmount the drive (if its even still mountable) and use dd to make an image of it. You can then mount the image and recover what you need to. If, for example, the dying drive is /dev/sdc1, then:
```
dd if=/dev/sdc1 of=/path/to/other/drive/image.dd
# Get some coffee
mount -t loop /path/to/image.dd /mount/point
```I just did this recently with a dying Raptor. Saved me a week's worth of work.

---

### Post by Mikael P. on 2009-09-28
That sounds really interesting. I presume I need as much space as the size of my dying partition. Is that correct?

---

### Post by Giblet5 on 2009-09-28
> **falconindy said:**
> Unmount the drive (if its even still mountable) and use dd to make an image of it. You can then mount the image and recover what you need to. If, for example, the dying drive is /dev/sdc1, then:
```
dd if=/dev/sdc1 of=/path/to/other/drive/image.dd
# Get some coffee
mount -t loop /path/to/image.dd /mount/point
```I just did this recently with a dying Raptor. Saved me a week's worth of work.


Good idea, but make sure you use the exact same replacement drive! eg, replace a WD3200KS with a WD3200KS.

Otherwise the partition information may be unreadable or the filesystem might be "fixed" in a bad way.

---

### Post by Giblet5 on 2009-09-28
Nevermind my last post. You said use a loopback...

Yes that will require as much free space as the original partion's total (used + free) size.

---

### Post by Giblet5 on 2009-09-28
> **Mikael P. said:**
> That sounds really interesting. I presume I need as much space as the size of my dying partition. Is that correct?

Yes. Total partition size, used+free.

Do you have am external USB drive?

I buy those 1TB "MyBook" USB drives at Sam's for $100 and use them to do daily backups of live 1TB partitions (I use rsync). Then, if a 1TB drive dies, I crack open the MyBook, rip the drive out, and replace the live partition, then buy a new MyBook (cheaper than the bare drive).

---

### Post by Mikael P. on 2009-09-28
Yes, that seemed logical. What is this loopback you are talking of. I guess this is it: mount -t loop /path/to/image.dd /mount/point ?
What does that command do? What exactly do the "-t" and "loop" stand for?

Is there somewhere I can go and read up on this dd command?

---

### Post by Giblet5 on 2009-09-28
> **Mikael P. said:**
> Yes, that seemed logical. What is this loopback you are talking of. I guess this is it: mount -t loop /path/to/image.dd /mount/point ?
What does that command do? What exactly do the "-t" and "loop" stand for?

Is there somewhere I can go and read up on this dd command?

A loopback device is a file treated like a device.

The 'dd' command (data dump) makes a byte copy of the input (if= option) to the output (of= option).

The idea is to create a byte-for-byte image of the failing partition and mount it like a device, then fix it with fsck, replace the failing disk, and copy the data from the mounted image to the replacement disk drive.

More on dd(1):
```
man dd
```

And loopback devices are discussed in the mount documentation:
```
man mount
```

---

### Post by Mikael P. on 2009-09-28
Thanks for the explanation of a loopback device. Is that what you specify with the loop switch?
Yes, I am aware of the man xxx command. But I am not using a linux system right now. (Though I guess I was lazy, it isn't that hard to google).

The fact that I write .../image.dd does dd know then that it should create an image file and not a whole new partition? I seem to find loads of cautionary tales in regards to dd. So I want to make sure I don't mess things up.

---

### Post by Mikael P. on 2009-09-28
Another question, as touched on earlier in this thread.

Why does a loopback device give me freedom not to use the exact same make and model of my dead HD?

---

### Post by falconindy on 2009-09-28
When you use the mount command, the -t flag lets you specify what **type** of device you're mounting. Is it ext3? Is it xfs? Or maybe, it's a loopback.

As mentioned, dd is creating a bit by bit copy of the contents of, in this case, the dying hard drive. Regardless of the brand, model, or protocol of the drive, a bit by bit copy is going to give you identical results. Mounting a device of type 'loop' simulates a block access device (which all hard drives are) to read the previously made image file. I'm not sure exactly what you mean in reference to bypassing the specs of your hard drive -- after the image is created, you're not accessing it.

dd won't create a new partition. It will, however, clobber another hard drive if that's what you specify the output as (e.g. /dev/sda1). Since the command I gave outputs to a file and not a hard drive, you're safe.

---

### Post by Giblet5 on 2009-09-28
> **Mikael P. said:**
> Thanks for the explanation of a loopback device. Is that what you specify with the loop switch?
Yes, I am aware of the man xxx command. But I am not using a linux system right now. (Though I guess I was lazy, it isn't that hard to google).

The fact that I write .../image.dd does dd know then that it should create an image file and not a whole new partition? I seem to find loads of cautionary tales in regards to dd. So I want to make sure I don't mess things up.


dd just reads input and writes output. It doesn't care whether it's a file or a device (typical unix philosophy). You could just as easily use other commands but dd is old-school and proven.

Almost everything is a file under linux... Devices are just special files (see the man page for mknod if you're curious).

The "image.dd" file will be created by the dd command if it doesn't exist. If it does exist, it will be overwritten.

---

### Post by Mikael P. on 2009-09-29
Thanks a lot for the explanations! I am learning a lot.

I was talking about "the exact make and model of my HD" as that seemed to be a prerequisite for an exact copy to function properly. But if I understand correctly that is not the case if I make an image instead of writing the whole drive to another drive.

---

