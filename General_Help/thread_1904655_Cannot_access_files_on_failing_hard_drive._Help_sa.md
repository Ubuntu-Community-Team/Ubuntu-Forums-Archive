---
title: "Cannot access files on failing hard drive. Help save my data!"
date: 2012-01-05
forum: General Help
---

### Post by PFiddles on 2012-01-05
Hey guys, nice to be here and all that other obligatory first-post jazz :)

My issue is that I cannot get past the Ubuntu loading screen (The purple screen with the dots, as I'm sure you're aware)

When I press Esc I see that there are a number of errors being reported on ATA1.00
Now, my secondary hard drive is a 250GB hard drive that I'm trying to recover some data from for my sister. Unfortunately, running CHKDSK in Windows for a couple of days we had a power outage. I read somewhere in the depths of the internet that Linux deals with hard drives in a different manner, and that perhaps using a Linux distro would be a way to reacquire the lost data. As I said, I'm new to Linux so I chose Ubuntu and installed that on a bootable USB drive. 

If anyone would be able to point me in a direction that assists me in reclaiming this data I would be hugely grateful!

Regards,
Tom

-EDIT-

Well. I kinda feel a bit silly now.

Ubuntu loaded after a while of waiting, I had just assumed because it was repeating the same error with no discernible difference between them that it had hung and was not going to load.

Now my issue is that I cannot see the hard drive in the 'Devices' section of the GUI's explorer. I've messed around in terminal a little bit, and I can see /dev/sda which appears to be the drive I'm after. It has a few partitions on it, one is the main partition (which has the data I'm after) it has a 'Recovery' partition and a 3rd partition I could not see in Windows that has something to do with Dell (it's a 2.5" Samsung drive from a Dell Studio 1535 Laptop).

Is there any way I can access the files on this hard drive through the terminal, grab everything out of the "Users" folder and be done with the blasted hard drive? I've not had much luck, but I'm going to keep trying!

---

### Post by sffvba[e0rt on 2012-01-05
*Thread moved to **General Help**.*


404

---

### Post by PFiddles on 2012-01-05
Okay, well the drive is now showing in the explorer, and I can traverse  it... Unfortunately when I've just tried to copy the /Users folder onto  the working hard drive the copy function doesn't work. Being a relative  Linux 'n00b', can anyone tell me what I can do to perhaps clean this  section of the drive as I'm trying to avoid a situation where I have to  leave the computer on for days on end, where it will be susceptible to  power outages ruining the progress again...

When I try to get to the folder in question /media/OS/Documents and Settings/%user%/ it will cd to the directory, but when I try to ls it just says "Input/output error". I'm assuming that's because the harddrive is dying, but I *REALLY* need those files :(

-EDIT-

I've had a quick look at the manual for DOSFSCK and regular FSCK, but I don't want to do anything to further damage the drive - seeing 
> Automatically repair the file system. No user  intervention  is  necessary. Whenever  there  is  more  than  one  method  to solve a problem,** the least destructive approach **is usedhas me a bit concerned...

---

### Post by PFiddles on 2012-01-05
[SIZE=1]<Accidentally replied instead of editing, woops!>[/SIZE]

---

### Post by kurja on 2012-01-05
Perhaps you'd be better off if you managed to mirror the dying hdd to a working one, then you could try salvaging data from the copy? ddrescue or clonezilla for an example.

Always try to minimize the amount of both run time and operations on a disk that is failing, it might stop working altogether at any moment - a bit of a worst case scenario spook there, but it's good to act cautiously if the data is important.

---

### Post by oldfred on 2012-01-05
If you go into Disk Utility what does it show. I just know that it should be green if you click on the drive/partition. If green then drive is probably ok and you can do repairs.

If a NTFS partition chkdsk is what you run first, but you may have to run it more than once as it does not fix everything on one pass. You have to rerun until no errors.

If a ext type partition you run e2fsck from a liveCD as it has to be unmounted.

If you can see partition, you should be able to copy some of it. Maybe copying each file rather than entire folder as any corrupted sector may prevent the entire folder from copying where most files may copy?

---

### Post by efflandt on 2012-01-05
I had 1 drive from an old laptop (boss' grandsons) that was failing (Windows refused to boot at all to protect what data was left) and it would not even automount or manually mount in Linux in the laptop (booting Linux from USB) or in external USB enclosure.  I let it sit for a week and on a whim, connected it in the external enclosure to my Ubuntu desktop, it automounted, and I was able to copy most of the users files from it, other than a directory or two related to some game.  Not sure if that directory was corrupted or incompatible file names.

When the replacement drive also began to fail, I was able to run chkdsk on it from Windows in the external enclosure (which only lost one file).  But clonezilla would not work to image the drive due to the bad sectors.  Seagate and WD have their own free versions of Acronis that was able to image the drive file by file (instead of every raw sector including bad ones), so I was able to restore the image to the warranty replacement drive.

Then the laptop refused to boot a 3rd time when Windows got infected with more than one virus, but chkdsk and a virus scanner were able to clean that up.

---

### Post by imachavel on 2012-01-05
> **PFiddles said:**
> Okay, well the drive is now showing in the explorer, and I can traverse  it... Unfortunately when I've just tried to copy the /Users folder onto  the working hard drive the copy function doesn't work. Being a relative  Linux 'n00b', can anyone tell me what I can do to perhaps clean this  section of the drive as I'm trying to avoid a situation where I have to  leave the computer on for days on end, where it will be susceptible to  power outages ruining the progress again...

When I try to get to the folder in question /media/OS/Documents and Settings/%user%/ it will cd to the directory, but when I try to ls it just says "Input/output error". I'm assuming that's because the harddrive is dying, but I *REALLY* need those files :(

-EDIT-

I've had a quick look at the manual for DOSFSCK and regular FSCK, but I don't want to do anything to further damage the drive - seeing 
has me a bit concerned...

I believe fsck is something you need to run at boot. I'm pretty sure you must connect your usb drive, then when grub appears, look for recovery options, then type in fsck. I'd imagine trading files between drives is fairly simple, not sure why you had to entirely install an entirely whole linux distro on an external flash or hd drive. Did you get all the files copied??

---

### Post by imachavel on 2012-01-05
> **oldfred said:**
> If you go into Disk Utility what does it show. I just know that it should be green if you click on the drive/partition. If green then drive is probably ok and you can do repairs.

If a NTFS partition chkdsk is what you run first, but you may have to run it more than once as it does not fix everything on one pass. You have to rerun until no errors.

If a ext type partition you run e2fsck from a liveCD as it has to be unmounted.

If you can see partition, you should be able to copy some of it. Maybe copying each file rather than entire folder as any corrupted sector may prevent the entire folder from copying where most files may copy?

no kidding, has to be from a live cd. get out of here, no wonder I couldn't get that to work. pop in cd, run e2fsck, select drive.

yes with ntfs you can run chkdsk /f :(drive letter) or chkdsk /r :(drive letter) e.g. chkdsk /f :c or chkdsk /f :f

also you can use list disk to check disks and volumes from cmd. Try it out for options as such:

list disk /? I believe that is correct. Best of luck

---

