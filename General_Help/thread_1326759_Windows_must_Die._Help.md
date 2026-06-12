---
title: "Windows must Die. Help?"
date: 2009-11-14
forum: General Help
---

### Post by Lu Seraph on 2009-11-14
How do I get rid of my dual boot and remove windows XP?

I only had a trial version of it on here and that is expired. I can't sign into it and I want it removed.

I only have an 80 gig drive on this old thing so having windows using 50g of it from the previous owner just seems retarded since I can't even log onto it.

Help me kill windows so Ubuntu can thrive!

---

### Post by Joe Ker1086 on 2009-11-14
There are a couple things you can do. Gparted can wipe out your windows partition pretty easily *BUT CAUTION* I blew out my whole partition table using gparted just by getting a little too hasty with the clicks. You could also download a program called Killdisk. It is a free program that you can upgrade to premium (but you will only need the free version) that does a 0 pass over whatever partition you point it too....but as with anything of its kind you must be SURE you are wipeing the right partition away...

---

### Post by Lu Seraph on 2009-11-14
Ok this is WEIRD
Got the partition editor on here now. 

I clicked on "Disk Usage Analyzer" and it's lying to me.
I only have an 80 gig hard drive.
When I was copying my windows file from /host.... and pasting them into my Document folder I was shown that I had 20 ish gigs left on my hard drive.
Which is why I want to get rid of windows. 

The Analyzer says I have a total 185 GB with 74.9 Used and 110.1 free.

Oh and the Gpart says I only have ONE partition and its 74 gb
I don't even have 110.1. What's going on!?!? I'm lost and frightened. 

Help me out of the woods here.

---

### Post by markjensen on 2009-11-14
Can you boot into Linux and post the output of the following command?

sudo fdisk -l

(that is a lowercase letter "L", not the number one)


This will list out your partition tables, and will help us see what is going on with your harddrive's setup.

---

### Post by Xog on 2009-11-14
It could be that you forgot the real size  of the hard drive :-D I did that with my laptop. I thought I had 80GB on this and when I installed ubuntu over windows I found out I have 120gb!

edit:

either I do only have 80GB and ubuntu's lieing to me like it is to you, or Windows was lieing to me and saying I had 80. :P

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris



*Note: A long time ago I did a dual boot with an older verson of ubuntu and I think I uninstalled it wrong, thus saying for the past 4 years or so that I have 80GB.. could be wrong :D

---

### Post by Lu Seraph on 2009-11-14
seraph@ubuntu:~$ sudo fdisk -l
[sudo] password for seraph: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea7c7571

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 7889 MB, 7889223680 bytes
228 heads, 43 sectors/track, 196 cylinders
Units = cylinders of 9804 * 4096 = 40157184 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         197     7704060    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 2) logical=(0, 1, 22)
Partition 1 has different physical/logical endings:
     phys=(119, 227, 43) logical=(196, 104, 23)
seraph@ubuntu:~$ 


I can ONLY boot into Linux, my windows is Expired. Yep it's 80gb!

---

### Post by Lu Seraph on 2009-11-14
Still need help, no idea what to do at all yet!

---

### Post by jeb800e on 2009-11-14
I have never heard of a *trial* version of Windows.

---

### Post by Rich_Roast on 2009-11-14
> **jeb800e said:**
> I have never heard of a *trial* version of Windows.

I have. Since XP they've always needed a licence key to be put in and verified after a period of about a month, or somesuch.

@ OP - the most straightforward way, if you can backup your personal data or you don't care about data on the partition, would be to hose the current partition by simply installing Ubuntu with the "use entire disk" option.

---

### Post by Lu Seraph on 2009-11-14
I was hoping it would not come to that, I have a lot of stuff on here that needs to be backed up and only a cd burner that hates my guts to do it with. Might have to wait until I buy a new external. Can't I just "Uninstall" Windows?

---

### Post by wilee-nilee on 2009-11-14
> **Lu Seraph said:**
> I was hoping it would not come to that, I have a lot of stuff on here that needs to be backed up and only a cd burner that hates my guts to do it with. Might have to wait until I buy a new external. Can't I just "Uninstall" Windows?

The master boot record may be in that windows partition so be careful, others can confirm this possibility.

---

### Post by julianb on 2009-11-15
Lu --

Your output from fdisk -l seems to say that you have two physical drives, dev/sda and dev/sdb

It also says that sda1 is formatted as NTFS (windows NT file system) and sdb1 is formatted as FAT32 (developed by microsoft, not a typical linux/unix filesystem).

And it says that sda1 and sdb1 (which are supposed to be the first partition of the first physical hard-drive and the first partition of the second physical hard-drive) EACH have about 80MB of space in total.

you DO NOT have to over-write a partition with zeroes in order to delete windows. if you simply format the partition on which windows resides (I am guessing it's the NTFS partition but I'm not sure!) then you will have deleted windows, and set the partition up to be used for any new files you like. Formatting is quick while over-writing all data with zeroes could take hours. 

Either way, it's recommended that files that you can't replace (by ripping again from CDs you own, downloading again from Gmail or internet site etc) be backed up somehwere. This is because hard drives fail sometimes and when they do it can be expensive or impossible to recover the data.

Note that formatting the drive on which windows resides will not change

I am assuming you DIDN'T install ubuntu with WUBI. If you DO have ubuntu-installed-with-WUBI, you can't get rid of your windows partition without deleting Ubuntu.

---

### Post by Neezer on 2009-11-15
> **Lu Seraph said:**
> I was hoping it would not come to that, I have a lot of stuff on here that needs to be backed up and only a cd burner that hates my guts to do it with. Might have to wait until I buy a new external. Can't I just "Uninstall" Windows?

I used gparted to reformat my windows partition...here is what my new fdisk looks like

```

nathan@lappy:~$ sudo fdisk -l
[sudo] password for nathan: 

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf9bc167

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       40492   325251958+  83  Linux
/dev/sda2           47014       48641    13076910   83  Linux
/dev/sda3           40493       47013    52379932+   5  Extended
/dev/sda5           40493       46741    50195061   83  Linux
/dev/sda6           46742       47013     2184808+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

The sda1 partition was my windows one....I reformatted it as ext3 then mounted it at /home so that my home folder was a second partition.


As to what willee-nilee said,

[quote=willee-nilee]
The master boot record may be in that windows partition so be careful, others can confirm this possibility. 
[/quote]

I recall having my vista partition denoted with a 'boot' in gparted....I was getting hasty and reformatted it anyways. I haven't noticed any problems though...I may in the future though.

Now I have enough space on /home to keep all kinds of music/movies/stuff. If I ever have to reinstall software, I don't need to worry about it cause all my data and storage is on a separate partition.

I guess all I can say is that I deleted my vista partition (this was put on my computer first) and I don't have any problems booting. I can't say for sure if it will work for you though....Good luck!


If you are interested in just making the old windows partition into a /home folder there are pretty good instructions in the thread that I started:
[http://ubuntuforums.org/showthread.php?t=1322810](http://ubuntuforums.org/showthread.php?t=1322810)

---

### Post by theozzlives on 2009-11-15
Did you install Ubuntu under Windows (WUBI)? If not, you can use the live CD to mount your NTFS partition and get your stuff off. It would just be a matter of deleting Windows with gparted and set the boot flag to your Ubuntu partition.

If you installed via WUBI, you'll need to back up your /home also, and just do a fresh install.

---

### Post by Mark Phelps on 2009-11-15
Unfortunately, your early responders failed to notice that your initial reference to /host was a clear indication that you installed Ubuntu inside MS Windows using Wubi -- which is why there is no second partition for Ubuntu.

Wiping XP, by default, wipes the Ubuntu installation as well.

Wubi is only meant as a trial of Ubuntu because, one of the major downsides of using that, is if MS Windows gets corrupt, you can no longer get into Ubuntu -- as you have learned the hard way.

If you have already formatted the XP partition, your Ubuntu install is gone and not recoverable.

---

### Post by Uncle Spellbinder on 2009-11-15
> **Lu Seraph said:**
> ...Can't I just "Uninstall" Windows?

No. Your best option would be to do as described above, *"if you can backup your personal data or you don't care about data on the partition, would be to hose the current partition by simply installing Ubuntu with the "use entire disk" option."* As quick and flawless as the Ubuntu install is, it will take no time at all.

And just to be clear on the "trial" of Windows. There is no such thing. Windows is not a shareware product. There is no 30 day "free trial" period. Yes, if you legally purchase the product you have 30 days to activate it. Microsoft gives you this time to ensure that you can get yourself connected to the internet during this time frame. Microsoft's 30 day activation period is in no way an invitation to try the product until the activation period ends.

---

### Post by wilee-nilee on 2009-11-15
> **Mark Phelps said:**
> Unfortunately, your early responders failed to notice that your initial reference to /host was a clear indication that you installed Ubuntu inside MS Windows using Wubi -- which is why there is no second partition for Ubuntu.

Wiping XP, by default, wipes the Ubuntu installation as well.

Wubi is only meant as a trial of Ubuntu because, one of the major downsides of using that, is if MS Windows gets corrupt, you can no longer get into Ubuntu -- as you have learned the hard way.

If you have already formatted the XP partition, your Ubuntu install is gone and not recoverable.

I think we all missed some key points he just wants Ubuntu.

---

### Post by Lu Seraph on 2009-11-15
Point and case, I don't have a code to activate windows. I don't want to, it's just useless on this system since I have other computers with windows and am not going to use it on here for anything.

So after I get all of my files of great importance off of this computer and onto a portable drive, I have found my ubuntu disk, what do I do?
I've never wiped a system clean with a dual boot/ and only an ubuntu disk at my disposal.

---

### Post by markjensen on 2009-11-15
What do you do when you are ready to install Ubuntu?

Put the CD in, make sure your BIOS is set to boot from the CD before the hard drive, then boot it.

Select Install.

Tell it to use the entire drive.

Get a sandwich and a drink.

Come back and see if it is done yet.

---

### Post by Lu Seraph on 2009-11-16
Haha Ok, I getcha. 
Just reinstalling Ubuntu will do the trick then once I've backed up?

Thanks!

---

### Post by Merk42 on 2009-11-16
> **Lu Seraph said:**
> Haha Ok, I getcha. 
Just reinstalling Ubuntu will do the trick then once I've backed up?

Thanks!

Yes.
Just back everything up first

When you reinstall and select Use Entire Disk, you will **lose everything**.  The plus side is once it's all done you'll have a more manageable partitioned system.

---

### Post by Joe Ker1086 on 2009-11-16
I dont think you can just uninstall windows....especially if you cant access the drive at all....what kind of data is on that drive that you want to save? audio, video, text ect?

---

### Post by louieb on 2009-11-16
> **Joe Ker1086 said:**
> I dont think you can just uninstall windows....

You don't uninstall any OS - you replace it. 

To the OP - **markjensen **in his post has it right. Replacing what you have now is as easy as popping in the Ubuntu CD and selecting install. BTW hold off on the sandwich - the installer will ask a few question - user name, time zone,  password.

---

### Post by Joe Ker1086 on 2009-11-16
> **louieb said:**
> You don't uninstall any OS - you replace it. 

To the OP - **markjensen **in his post has it right. Replacing what you have now is as easy as popping in the Ubuntu CD and selecting install. BTW hold off on the sandwich - the installer will ask a few question - user name, time zone,  password.

I was replying to an earlier message by lu....didnt look at the 3 other pages...

---

### Post by Puzzled Guy on 2009-11-21
Install gparted with this:
```
sudo apt-get install gparted
```

Then, using gparted, delete the windows partition, it is usually labeled OS_install

Be careful not to delete the wrong partitions though

If you have dual-boot with ubuntu, you will also have to rewrite the master boot record. Sorry though, can't help ya there

---

### Post by jacobs444 on 2009-11-21
you need super pe boot disk, i can send will boot xp live disk with locksmith to change password and then can login.

---

### Post by Lu Seraph on 2009-11-22
Thanks everyone I figured out how to back all my stuff up and will be reformatting soon. I just have one little issue to solve, will post  new thread.

---

