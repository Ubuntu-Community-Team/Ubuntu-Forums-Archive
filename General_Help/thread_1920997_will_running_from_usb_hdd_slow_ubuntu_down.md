---
title: "will running from usb hdd slow ubuntu down?"
date: 2012-02-05
forum: General Help
---

### Post by LLCoolJeff on 2012-02-05
OK I think I phrased the subject a little wrong, I know it will slow it down, but to what degree? My machine is not that old ('09) so it can run at a decent speed, just not sure if I should install alongside windows on my hdd, or use one of my external usb hdd's which is what I'd rather do.

What are your opinions?

---

### Post by aasdfasdfg on 2012-02-05
Is the external drive a pen drive (<32 GB) or a full-fledged external hard drive? I think that would affect my decision.

If the process for setting up a dual-boot environment is the only thing that's holding you back, I would recommend giving it a try; I, for one, consider a dual-boot more convenient than having two separate "devoted" drives. Some benefits of a dual boot:

[LIST]
[*]Easily access your files from Windows and from Linux
[*]If at some point you manage to crash windows or mess up your settings in Linux, you can boot into the other partition and have a shot at fixing everything
[*]Better performance than booting off of an external hard drive
[/LIST]
Of course, here are some cons:

[LIST]
[*]If free space is an issue, it may not be feasible
[*]Setting up the dual boot may be a bit of a time-consuming project
[*]Less portable than having an OS on an external hard drive
[/LIST]
Personally, I always lean towards setting up dual-boots: I think I have done this on 5 or 6 different machines for personal use since I started with Ubuntu five years ago. I have also set up Windows/Linux dual boots in a work environment multiple times. Overall, I have not had any issues this whole time and I think the process is pretty safe.

---

### Post by LLCoolJeff on 2012-02-06
yea, my external drive is an actual hdd, not a small flash stick. 

Its funny you mentioned not having any problems, that is the reason why I am thinking about booting from external drive, so I dont have the grub menu. 

I accidentally messed up a past installation by running the wrong boot parition which was called vista loader, it totally messed up the grub giving me a grub recovery(?) prompt on booting, It took me forever to fix, and I never want to go through that again from accidentally clicking the wrong one.

I think for now I will go with the external hdd unless I notice a big performance drop and then I will maybe switch.

I think it's also nice having it boot from usb so I keep my internal hdd untainted, and all I have to do is remove the usb drive before booting and Its like it was never there aka dont have to worry about the grub.

---

### Post by TheFu on 2012-02-06
USB2 is slow. It will be painful. 
USB3 is faster, but I've had queuing issues with it.  Basically, under USB3 asking the HDD to do more than 2 things at the same time can cause everything to stop for 20+ seconds. EVERYTHING.  This could be a HDD or USB3 controller issue, I dunno.

I'd strongly suggest that you make room on a SATA or eSATA HDD for Linux.  It is really amazing what a 10GB partition for Linux OS+Apps can accomplish.  You can access NTFS partitions for data if necessary. I've been running my main desktop on 10GB for the last 3 yrs.  Large data files are stored elsewhere, obviously.  Just a few months ago, I increased it to 14GB. I expect that will last a few more years.

Most of my virtual machine servers fit in 4GB easily.
When you create the linux partitions, make an Extended partition then place the Linux OS and swap into logical partitions inside there.  Read up on the differences if you don't already understand. Linux boots from logical partitions just fine.

---

### Post by aasdfasdfg on 2012-02-06
> **LLCoolJeff said:**
> 
Its funny you mentioned not having any problems, that is the reason why I am thinking about booting from external drive, so I dont have the grub menu. 


I see; given your experiences with grub, I can understand not wanting to deal with it. Using the external hard drive should be fine in practice. Do you need any tips with partitioning the external drive, or will you just be wiping it and doing a default install?

@TheFu: I see you are quite the Linux hipster. Linux was little more than Linus' pet project in 1993, correct?

---

### Post by Mark Phelps on 2012-02-06
To give you some typical data transfer numbers for comparison:

SATA II speeds: 2.4GBits/sec or 300MBytes/sec

USB 2.0 speeds: 320GBits/sec or 40MByts/sec

So basically, an internal SATA II drive has the potential for transferring data about 8 times the speed of the same drive connected via USB 2.0.

Does this mean that an OS on an internal drive will really perform 8x as fast as the same OS on an external drive? In reality, probably not -- as real-time performance is more than just raw data transfer speeds.

So, you might not see a slow-down of that magnitude, but it will be slower using an external USB 2.0-connected drive.

---

