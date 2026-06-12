---
title: "Error On Disk??"
date: 2011-07-16
forum: General Help
---

### Post by ken0069 on 2011-07-16
OK so I've got a multiboot computer with Windows XP and Ubuntu 9.xx that was upgraded online to 10.xx back about 6 months or so ago that has started doing file scans at boot up about once a week.  Two days ago it was really slow booting up so once it finished I restarted it and it booted “ok” that time although it may have been a little slower than normal.  Not a big deal

Well, last night when I booted it there was a prompt that came up stating that I needed to strike the F key to see if Ubuntu could fix some system errors, or something to that effect.  After it finished it booted up and I did what I had to do and shut it down around midnight.  

So today, thinking this disk was going bad I went looking for a way to clone this Ubuntu load to another disk I have and it was recommended that I use one of several tools to do this.  I've tried a couple of them but they say there is an error on the drive and the last one I tried is Symantec Image Center and it gives me the following message when I try to run it.

(quote)“Symantec Image Center has found an extended partion on disk 1 that crosses the 1024 cylinder boundary and is not marked as an Extenced X partition.

This condition can cause data corruption on this disk.

After fixing this error Symantec Image Center must reboot your system to reinitialize the file system drivers.

Would you like for Symantec Image Center to change the Extended partition to an Extended X partition?”(/quote)

So my question is will this mess up my Disk 1 Ubuntu load?  

And is this indeed the reason I keep getting file system scans on that drive?  It passes SMART at boot up so I'm guessing that the partition error is what is causing this?

Should I let Symantec fix it or not?

Thanks,

Ken0069

---

### Post by psusi on 2011-07-16
It sounds like this program doesn't know what it's talking about.  The BIOS will only complain if the disk indicates that it is going to die soon.  Open the disk utility and look at the actual SMART values and see if you have any bad sectors, and run the long self test.

---

### Post by lmarmisa on 2011-07-16
I agree with psusi's proposal.

In relation with a tool for cloning your disk, consider to use Clonezilla Live:

[http://clonezilla.org](http://clonezilla.org)

This is a Live CD/USB based on Debian. It works great with both Windows (FAT, NTFS) and Linux/GNUs (EXT3, EXT4, etc) filesystems.

---

### Post by ken0069 on 2011-07-17
> **psusi said:**
> It sounds like this program doesn't know what it's talking about.  The BIOS will only complain if the disk indicates that it is going to die soon.  Open the disk utility and look at the actual SMART values and see if you have any bad sectors, and run the long self test.

SMART data shows there are 545 bad sectors on this 80GB Segate ATA drive.  The overall assessment states only that "the drive has a few bad sectors"?  I don't know how many there are total for this size drive but I do know that it's normal to have some number of bad sectors even on a brand new one.  

Was wondering if that error the Symantec progie is seeing is this group of bad sectors that aren't formatted in Extended X?

Ennywho, it was slow as a snail booting again this morning so I'm going to run that surface test to see how many more bad sectors show up.  

Meanwhile, I'll look for clonezilla too and see if it's something I can use but with those other programs not working with the disk error I'm not very optimistic.  

I'll post back here once that surface test is done.

Thanks ppl  

Ken

---

### Post by psusi on 2011-07-17
Sounds like you need to replace the drive.

---

### Post by ken0069 on 2011-07-17
Well, I have good and bad news.  Bad news is that when I ran the scan that drive showed 11 more bad sectors so I guess it's going to take a dump in the not too distant future.

Good news is that Clonezilla ROCKS!!!!  I just got done cloning that bad drive to a good 120 GB WD that I had laying around and the best part of it was that Clonezilla even copied the Grub 2 boot loader over, something that other clone tools DID NOT do!  

Ennywho, there is joy in mudville again and I just want to say thanks a million for the link to Clonezilla's website!!  Next Windows clone job I do I'll try it on that also.  I'm impressed!!

Ken

---

### Post by lmarmisa on 2011-07-17
Hi ken0069,

I am happy because you like Clonezilla. BTW, Clonezilla is a fine tool not only for cloning disks but also for making backups of disks and partitions.

If you do not need more help about your problem, please mark the thread as SOLVED.

Best regards,

Luis

---

### Post by ken0069 on 2011-07-18
> **lmarmisa said:**
> Hi ken0069,please mark the thread as SOLVED.

Best regards,

Luis

Don't know how to do that?  Tried to edit my original post and adding "Solved" to that original heading but wasn't allowed to do that so I marked the previous post as "RESOLVED" as it wasn't really a problem with Ubuntu as such, just a bad drive.

If this isn't sufficient then please tell me what and how to do what you want done.

Thanks,

Ken

---

### Post by lmarmisa on 2011-07-18
> **ken0069 said:**
> Don't know how to do that?  Tried to edit my original post and adding "Solved" to that original heading but wasn't allowed to do that so I marked the previous post as "RESOLVED" as it wasn't really a problem with Ubuntu as such, just a bad drive.

If this isn't sufficient then please tell me what and how to do what you want done.

Thanks,

Ken

Look at Thread Tools. I think that you have the option Mark as SOLVED there.

Best regards,

Luis

---

