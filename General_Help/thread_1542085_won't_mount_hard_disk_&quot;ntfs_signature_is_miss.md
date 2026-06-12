---
title: "won't mount hard disk &quot;ntfs signature is missing&quot;"
date: 2010-07-30
forum: General Help
---

### Post by ZenStephanie on 2010-07-30
Hello all,

I have been trying to use Ubuntu to recover my broken Windows PC.

Windows was not rebooting, I was getting only a blank screen.

I just got an external HD and backed up my entire hard disk to it.

After that, I started to try a few things, and now wish I hadn't...

Followed the directions on this website:

[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

I tried using the commands in the last post of the thread, then rebooting.

Now I get an error: 'no operating system detected' when I try to boot from the HD.

But that's not even the big deal... now I can' even see or access my hard disk from Ubuntu! I was able to do so before I tried the above.

Looked up instructions for how to manually mount the disk.

When I try them, I get the error "NTFS signature is missing."

I guess I damaged the NTFS signature when I executed the sys-linux and mbr commands?

When I do fdisk -l, this is the output I get:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4863    39029917+   7  HPFS/NTFS
I've thought of just wiping the whole HD and installing Ubuntu and forgetting Windows... but I'm nervous about the stability of my backup files, as it's possible a virus may have been what took my computer down. And I can't get any AV programs to work properly from Ubuntu (which now is almost pointless as I can't even connect with my hard disk from Ubuntu now).

Can anyone help me regain access to my hard drive through Ubuntu?

---

### Post by P4man on 2010-07-30
Try testdisk. you can install it from the livesession (assuming you have internet connectivity), its in the repo's you can just install it with
```

sudo apt-get install testdisk
```

Then run it

```
sudo testdisk
```

follow instructions here:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

But im a bit confused about what you are trying to achieve. You already backed up your files to an external drive no?

---

### Post by ZenStephanie on 2010-07-30
Got error: "E: couldn't find package testdisk"

I guess download it from a site? Thanks for the help!

My goal is not to unnecessarily wipe the Windows portion of my machine.

I believe that only the boot sector is damaged / infected / corrupted, and think it would be a waste...

I have some old archive files that may only be usable in Windows.

Another thing... I will need to do a hard disk install of Ubuntu to be able to even have a shot of getting an antivirus program to work on it.

And that will require me to partition my hard drive. Which (a) I don't know how to do without wiping files and (b) I have only 3-4 GB of free space to work with, and would need to be able to access the disk from Ubuntu to delete files from it first to free up more space.

At this point, I don't know if Windows is even salvageable... I have some peace of mind that my files are now backed up, but I don't trust that the external HD will never get damaged, corrupted, etc. I've read too many horror stories...

Maybe what I'll have to do is a full install of Ubuntu and just wipe Windows... but I realize I don't even have a windows install disk (I have a partition on the HD with the contents of what would be on the install disk that I now can't access), so if I do that, there's no shot of being able to use Windows ever again on this computer without buying a new edition of it, which I can hardly bring myself to do.

And it's not that I'm such a Windows fan that I have to use it... I'm actually planning on getting a Mac for my next computer, which means, again, a lot of my old archived files from the last ten years or so won't be accessible from that computer.

Basically, I'd just like to give a shot of being able to salvage Windows and run the computer as a dual boot before giving up on Windows and installing Ubuntu only and erasing the hard drive.

---

### Post by ZenStephanie on 2010-07-30
Wow, testdisk is awesome! Problem (well, this particular problem) is fixed, hard disk can once again be mounted with Ubuntu.

As a noob, I definitely appreciated the step-by-step instructions :D

Thanks again, I will now continue moving forward with figuring out how to get Windows up and running again... can testdisk also be used to get past a 'black screen of death' with Windows? That probably needs a new thread...

---

### Post by dino99 on 2010-07-30
Windoz, whats that ?

ubuntu+wine run smootly your exe apps

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by P4man on 2010-07-30
> **ZenStephanie said:**
> Wow, testdisk is awesome! Problem (well, this particular problem) is fixed, hard disk can once again be mounted with Ubuntu.

As a noob, I definitely appreciated the step-by-step instructions :D

Thanks again, I will now continue moving forward with figuring out how to get Windows up and running again... can testdisk also be used to get past a 'black screen of death' with Windows? That probably needs a new thread...

Dont even know what a black screen of death is, but if its a bootloader problem or even something else, I would suggest booting from a windows cd and running the recovery tools from there. fixmbr or fixboot I think its called if its just a bootloader issue.

And yes testdisk is awesome. But just for partition and filesystem problems its not a miracle solution to repair windows ;)

---

### Post by ZenStephanie on 2010-07-30
Black screen of death is a boot issue, at least as far as my limited, beginner research and knowledge goes.
 
Basically, I had a virus, Avast 4.8 cleaned it, so I thought I should install the new Avast. After I installed Avast 5.0, my computer wouldn't boot Windows. It wouldn't even show the Windows logo, it would just go to an entirely black screen and stop. I don't have the boot CD and I tried using the Recovery Console offered on the Microsoft site you can put on six floppy disks, it would read them but stop at the sixth and not go further, saying Windows had to shut down due to a virus. I don't know if it really is a virus or if (a) it's reacting to a damaged boot sector or (b) one of the Avasts is treating the other like it's a virus. I didn't realize you had to manually uninstall the previous version of Avast and have heard double installs of Avasts can mess with Windows. So now I'm stuck trying to figure out how to get Windows to run again.
 
I want to do a dual boot of Avast and Windows, but I'm nervous about it as I have no idea how to partition the hard disk to avoid data loss or problems. I only have about 3-4 GB of free space left on the 40 GB hard disk (it's an old computer, Dell laptop circa 2003). So I'm figuring out what and if I should manually delete. Probably music files--take up the most space, and even though it would suck to lose them, it wouldn't suck as much as losing personal pictures and documents.
 
And I don't want to just wipe the data and start again because in my mind, the whole idea of having a backup is that there's more than one instance of the data in existence. External hard drives can be faulty, etc. And I really would like to be able to get into the old Windows system, especially since I can't seem to get Ubuntu to detect my wireless connection properly.
 
I suppose learning how to partition correctly is just a matter of the right research. But there was really no point if I couldn't mount the hard drive and access the files from Ubuntu, so thanks again for pointing me in the right direction.

---

