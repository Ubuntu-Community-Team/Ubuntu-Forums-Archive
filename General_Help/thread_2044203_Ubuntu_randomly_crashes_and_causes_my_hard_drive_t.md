---
title: "Ubuntu randomly crashes and causes my hard drive to go into read-only mode"
date: 2012-08-19
forum: General Help
---

### Post by Valkhorn on 2012-08-19
For a few weeks now my Ubuntu 12.04 system has been locking up. The hard drive seemed to keep locking up and going into read-only mode. I have to reboot in order to keep working on it.

So, I decided to just clone the hard drive and see if I can recover it. 

When I do a regular copy of all files from the drive to another, it gets to about 110 megs in and gives me an input/output error. It pretty much just stops reading and I have to reboot the computer to get the hard drive mounted again. 

I've ran fsck with the options -fy on it several times and it shows no errors. The hard drive doesn't make any noise when this happens nor does it power down. I've tried dd-rescue, but it looped through the entire drive 3 times without copying anything so I assume it had the same input output error.  I'm able to boot into Ubuntu with the original drive even though it has a bad habit of going into read-only mode randomly after I boot into it. Sometimes it locks up a few minutes into using the computer, last week it took a whole week of working on it before anything happened to it.

I've tried to clone a partition with GParted, and it pretty much stops after 110 megs and tanks, causing GParted to lock up. Clonezilla has been no help either, because again it'll just cause an input/output error and the files can no longer be copied.

Is there an fsck command or anything I can do that might catch and fix what the problem is, or at least copy files over while ignoring a potentially bad sector? It seems like it's the same file and the same place on the hard drive, so surely fsck should be able to catch it?

Let me know if you guys have any ideas. Thanks!

---

### Post by darkapec on 2012-08-19
i would think fsck would catch any errors... the only other option I can think of is using HDD regenerator, it is a great piece of software and it will verify sector by sector to see if your drive has any broken sectors and will attempt to repair them. 

There is a trial version of the software, you will need a windows environment to install the software and create a bootable cd from within. The trial software is only set to fix 1 bad sector... good news is this will check your whole drive and you will know if this is causing you issues. Bad news is if you have multiple bad sectors, you will have to reboot a lot and keep running the software to repair 1 bad sector at a time or spend some money to get the full version. 

I stand behind this software, my business has used it for years with excellent success.

---

### Post by Valkhorn on 2012-08-19
> **darkapec said:**
> i would think fsck would catch any errors... the only other option I can think of is using HDD regenerator, it is a great piece of software and it will verify sector by sector to see if your drive has any broken sectors and will attempt to repair them. 

There is a trial version of the software, you will need a windows environment to install the software and create a bootable cd from within. The trial software is only set to fix 1 bad sector... good news is this will check your whole drive and you will know if this is causing you issues. Bad news is if you have multiple bad sectors, you will have to reboot a lot and keep running the software to repair 1 bad sector at a time or spend some money to get the full version. 

I stand behind this software, my business has used it for years with excellent success.

Thanks. I may try that tomorrow. I just hope nobody asks me to cut and paste the output since this is on an entirely separate system.

I have a windows machine so I can try this for sure.

---

### Post by Valkhorn on 2012-08-19
I just did a few things using the Ubuntu Repair Live CD:

At the command prompt I typed

sudo fsck -f /dev/sda1

No problems were reported.

However, I typed in

sudo e2fsck -f -c /dev/sda1

And at about 3% in I get some strange errors:

<6> [N.N] sd 0:0:0:0: [sda] 

Or

<6> [N.N] sd 0:0:0:0: [sda] Read(10) (some address)

Where N.N is some integer dot integer pattern. 

Now it keeps spitting out these errors so I'm not sure what's going on. How come fsck didn't catch something e2fsck did, and what are these messages and what do they even mean?

---

### Post by Valkhorn on 2012-08-19
Still nothing. I ran the program HDD Regenerator and it found no bad sectors on the drive.

I re-ran fsck and it found no problems. Yet, running e2fsck with the -c option gave out a lot of output errors.

It seems like the drive goes to a certain point no matter which folders I try to copy and then switches to read-only mode. And, even in read-only mode, I can't seem to copy files at all.

The files are pretty much intact, yet I can't seem to access them to copy the files over to recover my data. 

Are there any suggestions as to what I can do to recover anything from this drive?

EDIT: I installed a fresh copy of 12.04 onto a new hard drive, and whenever a copy crashes it turns the original hard drive into a read-only file system. This makes no sense. Why would it do that? Do I have possibly a bad motherboard?

EDIT2: This might help someone later on. Out of sheer frustration I tried another motherboard I had laying around the house. I'm doing a test copy of about 20 gigs worth of files from one drive to another. It seems like it's working so far. The test copy is up to 8 gigs and a file copy NEVER got that far before on the old motherboard.

To help others who had a similar problem I did the following

1) Test to see if the issue is on one hard drive or several. 
2) If it's on one hard drive, run e2fsck -fc on the drive to check it for errors
3) If there are no bad errors, and you plug in another hard drive, run dd rescue. If dd rescue loops more than once, or gives you random "sd" errors as I listed above, then it's possibly a sata port or motherboard issue
4) If you run GParted, and are unable to copy a partition or resize a partition, but you're still able to use the drive and fsck turns up nothing...
5) Try another motherboard!

If Ubuntu switches your drive to 'read-only', or switches your OS drive to 'read-only' when you know that drive is fine, then chances are your own drive is fine, and your motherboard is going bad.

You could also try a SATA card to bypass the onboard SATA ports, but I didn't have one laying around that I could use.

Now comes the fun part of copying everything to a new drive again.

I won't mark this as solved until I can copy an entire drive without error, but so far it looks good.

---

