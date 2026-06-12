---
title: "Lynx 10.04: File system failure after power outage"
date: 2010-06-08
forum: General Help
---

### Post by sirpixalot on 2010-06-08
I recently installed Lynx 10.04 amd64. Twice now, my entire file system has become unusable -- each time after a short power outage (2 seconds). 

In the first setup, I had two primary partitions: 1) / that was ext4; 2) /home that was ext4.

In the second setup, I changed the /home to ext3.

Both times, after booting up following the power outage, I received a message saying that "serious errors" were found in /home. But, after several reboots, I was able to login and use the system. Then, some time later, I would started getting "Read Only" messages when trying to write to the file system.

fsck gave the following message: "/home terminated with status 4". I received numerous "I/O error" on sda messages.

My question: Is this vulnerability due to using ext4 or is it related more to something else in Lynx 10.04? Further, what can I do (other than buying a power backup device) to avoid my file system becoming unusable after a power outage?

Thanks for your help.

---

### Post by bodhi.zazen on 2010-06-08
First I suggest you run fsck from a live CD

```
fsck -y /dev/sdxy 
```

Where sdxy = your root or home partition.

I also advise you get a power backup, but then only give you a few minutes to shut down.

The only other solution is - Back up your data to an external driver (flash or CDROM).

---

### Post by sirpixalot on 2010-06-08
Judging from your reply, should I assume that this is a known problem and that it is accepted by the Ubuntu community?

I have never used an operating system that accepts that the file system will be lost in the event of a power outage.

---

### Post by bodhi.zazen on 2010-06-08
> **sirpixalot said:**
> Judging from your reply, should I assume that this is a known problem and that it is accepted by the Ubuntu community?

I have never used an operating system that accepts that the file system will be lost in the event of a power outage.

I would go further then that. File system corruption is a known problem across all file systems and operating systems.

It is not an "accepted" problem, but there is no solution from a hardware or software design.

Why do you think people use power back up ? Loss of power can cause file system corruption as well as hard ware failure.

---

### Post by LowSky on 2010-06-08
> **sirpixalot said:**
> Judging from your reply, should I assume that this is a known problem and that it is accepted by the Ubuntu community?

I have never used an operating system that accepts that the file system will be lost in the event of a power outage.

This can happen in Windows as well. Except windows will just show the wrong time in the right hand corner, and BSODs!

The file system isn't lost. In fact you dont need to use a Live CD you can boot into recovery mode and repair the drives from there if you like.

This error can occur when the time on the machine is older than the time on the hard disk. Which means that your BIOS was reset or its battery is dead and the time isn't correct. For example, the BIOS says 12PM on JAN 1 but the hard drive says its 2:33AM on June 8.

So an even simpler fix is to check BIOS and fix the date and time there, and if still required run the command the user above.

---

### Post by sirpixalot on 2010-06-08
I tried the following command.

> ```
fsck -y /dev/sdxy
```

fsck appeared to fail and complained of something along the lines of "short read".

I was unable to mount the partition in "recovery mode".

Using a LIVE USB, I was unable to mount the partition.

This type of failure has now occurred twice in a three week period -- each time with a fresh install of Lucid Lynx 10.04.

I never had such problems with 8.10.

---

