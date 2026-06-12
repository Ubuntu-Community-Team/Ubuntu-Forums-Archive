---
title: "No root file system is defined???"
date: 2011-08-06
forum: General Help
---

### Post by mcman56 on 2011-08-06
I'm trying to install 11.04 and get the error warning in the title.  It says "Please correct this from the partitioning menu. "  How do I do that?  I don't see any options for that.  Puppy will already boot from that device and has grub installed.

---

### Post by garvinrick4 on 2011-08-06
What does your partition table look like?
Are you trying to make more than 4 primary partitions maybe.

---

### Post by mcman56 on 2011-08-06
No,  it shows no space for sda but then has a sda 1 through 4.  Would less be better?  sda4 is unknown/ unallocated.  The hard drive seems to have an issue so I tried to partition around that........with my very limited experience and knowledge.

---

### Post by Basher101 on 2011-08-06
then you have 4 primary partitions from what i can tell. Try to delete sda4 and create an **extended** partition (when in gparted in the upper right you can see Logical partition, click on it and change to extended) then proceed the installation in the extended partition.

---

### Post by garvinrick4 on 2011-08-06
> No,  it shows no  space for sda but then has a sda 1 through 4.  Would less be better?   sda4 is unknown/ unallocated.  The hard drive seems to have an issue so I  tried to partition around that........with my very limited experience  and knowledge.
 		                   		  		  		 		 			 				__________________
There are 3 types of Partitions, primary,extended,logical. You can only have 4 primary partitions per drive.
Primary and extended are counted as primarys. Extended is a house for logical partitions which you can have all you want. Linux can live in logical partitions. Windows likes its own
primary partition sda1 thru sda4 are primary. There is no sda that is the drive and where the bootloader lives called an (mbr) master boot record. sda5 and up are logical partitions.
So all you need in Linux is one extended partition and put all the linux ones in there in a logical partition. 
Most all systems comes with Windows pre-installed and most take up at least 3 primary
partitions from the get go. 
If there is a sda4 unallocated right click on it and make a NEW partition and make it EXTENDED and then right click on the EXTENDED partition sda4 and make LOGICAL partition, You have to hit apply arrow after each exercise  to make apply it.
#When you use gparted or any partitioning tool focus because you are messing with your harddrive and once it is done its done.

---

### Post by mcman56 on 2011-08-06
make a NEW partition and make it EXTENDED and then right click on the EXTENDED partition sda4 and make LOGICAL partition,

sda4 shows as logical but I don't see the other options you mention
I still get the same error

---

### Post by Basher101 on 2011-08-06
Okay, if you have not deleted it ofcourse it will not work. Delete it and follow garvinrick4's instructions > If there is a sda4 unallocated right click on it and make a NEW partition and make it EXTENDED and then right click on the EXTENDED partition sda4 and make LOGICAL partition, You have to hit apply arrow after each exercise to make apply it.
 #When you use gparted or any partitioning tool focus because you are messing with your harddrive and once it is done its done.
If you still can't do it i will explain with screenshots (just gotta find an usb stick i can delete...)

---

### Post by Miljet on 2011-08-07
> No root file system is defined
That error message usually means that you forgot to check the box to tell the installer what to mount. Just find that box and select "/" (forward slash) to tell it to mount the root file system.

---

### Post by mcman56 on 2011-08-07
The forward slash resolved that issue but what does that mean?  /Boot made more sense to me.  

Unfortunately, it hangs about 2/3 through the "copying files" portion.  I think I have a bad spot on the drive and everything stops when it gets there.

Thanks

---

### Post by Topsiho on 2011-08-07
From what is already written in this thread I understand that there were 4 primary partitions on the disk, and that means that no more partitions could be added, for Ubuntu to be installed in.

Also I get that one, probably the 4th primary partition (sda4) is wiped, and that in the space that became free a number of logical partitions, sda5, sda6, etc are created.

I read that the copying of files, during the actual install, stops after 2/3 of the files are copied.

That can be explained by not having enough space for the files to be installed in: is the partition for / large enough?

So you have to make sure:

partition / is larger than say 5 GB, better is 10 or even some more, if there is room enough for it.
Then you need a swap, make that 2x your RAM.
And the remaining space should be for a /home partition, in which will come all the personal files of the users of your computer. The more space, the more you can store into it. A separate /home partition enables you to keep these files whenever you do another install, new version of Ubuntu, or other distribution. Just not format it.

If there is not enough space, than you should first create more space, by making the previous primary partition (sda3?) smaller, and extending the container (extended partition) of the logical partitions with the space that comes free (gets unallocated).

Someone asked you for your partition table, but you did not give it.
You could also give a screenshot of GParted, showing the situation of your disk, so we get a better picture ( :) ).

Topsiho

---

### Post by Miljet on 2011-08-07
> The forward slash resolved that issue but what does that mean? /Boot made more sense to me. 
The forward slash stands for "root", or in other words the top of the file system. /Boot is a sub-directory under root as indicated by the forward slash in front of it. /Boot/grub would indicate a directory called grub, which is located in the boot directory, which is located under the root directory.

More info here if you are interested: [http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html](http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html)

---

### Post by mcman56 on 2011-08-08
I have been through several versions of partitioning.  This last time I set it up as you described; 15 G for Ububtu, 2 G for swap and the remainder as one more.  It loaded and seems OK.

Unfortunately, I'm still confused.  The original dual install with XP totally died so I tried reloading giving the whole drive to Ubuntu.  The install failed and the system was no longer functional.  I used puppy/ gparted to partition the drive and tried to reload but there was always a failure.  (The system was not functional so I could not get any screen prints.)  Using puppy/ gparted again, I would see more partitions with some of them locked.  I guess this is what a failed install leaves.  I repeated many times with different partition options.  Sometimes the partitioning failed which led me to believe there could be a drive issue.  It always seemed to be the last partition so I tried leaving some unformatted space at the end but it seemed to make no difference.   I realize that this was not a very methodical approach but I'm just a beginner stumbling through.          
I

---

### Post by Topsiho on 2011-08-08
I am sorry to read that your install is not sucessfull yet.

Maybe you can give us the result of

fdisk -l

as root, or using sudo, in puppy or terminal of Ubuntu, or else.
This should give a view (partition table) of the partitions on your disk, such as, for my disk:

Schijf /dev/sda: xxxx GB, xxxx bytes

--
--

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        2677    21502971   83  Linux
/dev/sda2            2678      121601   955256968    5  Uitgebreid
/dev/sda5          120837      121601     6144862+  82  Linux wisselgeheugen
/dev/sda6            2678      120836   949112104+  83  Linux

In this you can see I have 1 primary partition (sda1), and 2 logical ones, within an extended partition (Uitgebreid).

Topsiho

---

### Post by mcman56 on 2011-08-08
No, the install did work.  However, now I need to create some folders in that big empty sda2.  "create folder" is grayed out in File Browser.  How do I proceed?  thanks!

---

### Post by Miljet on 2011-08-09
It is quite impossible to tell you how to proceed when we don't know where you are at. Please post either the results of "sudo fdisk -l" or a screenshot of your gparted screen.

---

### Post by Topsiho on 2011-08-09
Exactly.

+1 to Miljet :)

Topsiho

---

### Post by mcman56 on 2011-08-09
I finally got this system on line.  A screen print is attached.  Thanks for your patience.  I seem to remain a beginner at this.  

The current issue is that   "create folder" is grayed out in File Browser for sda3

---

### Post by Topsiho on 2011-08-09
Great. See that you use all the disk space for Linux now.
I guess 16 GB for /, 2 GB for swap and the rest, 142 GB for /home, which is great, if your RAM is 1 GB.

You cannot edit these partitions from your installed Ubuntu, because they are mounted. So you can't edit sda3, I think you can't unmount this partition because it should be there, e.g. to look up your personal configurations.

Editing is possible from the live disk however, if you still want to do so.

Great you have a running Ubuntu now, but you have lost your Windows, if you are sorry for that.

If you still want Windows, however, you need to install it first, I am afraid, and start all over again. With a lot of experience now, so it gets easier and easier to do, and so you'll soon be able to help others :)

Maybe someone else on the forum can tell you whether you really have to start all over again, installing Windows first, if you still need Windows.
I myself do (some unintelligible muttering from behind tightly closed lips here) because manufacturers of electronic hardware often/always  refuse to support Linux, such as Windows and sometimes Mac.

Topsiho

---

### Post by mcman56 on 2011-08-09
I do not want to edit the partitions.  I want to save things to the big partition.  I would also like to be able to create folders on the big partition.  However, the system will not let me do either.  It shows as mounted but I have no access.  See the screen shots.  (I renamed it private.)  Do I need to unlock it somehow?  Thanks

---

### Post by Topsiho on 2011-08-09
So Ubuntu uses two partitions, the 16 GB one (sda1) for /, and the swap partition, sda2. And sda3, the big partition is mounted on /media/private.

OK.

The you can't make folders on this because it is not yours. You only own /home/<your login name>.

You'll have to read about permission. permissions for owners, groups and others, to read, write and execute. You need permission to write for the media/private folder.

You should see man chown, and man chgrp for this.

But why don you use your /home for this? and why did you not use the big partition for your /home?

Topsiho

---

### Post by mcman56 on 2011-08-11
I tried using chown several times but it did not "seem" to work for a partition.  However, I have discovered that I can not write to /media but can write to media/private.
Good News = this will work for me
Bad New = I'm not sure how I accomplished the task

Is there some type of permissions report I could get?  I looked in the GUI but don't see any functions for that.  Thanks for your patience.

---

### Post by Topsiho on 2011-08-11
I am sorry, but this is not the way to go, if I understand you correctly (which several times now I did not, for which I apologize).

/media/whatever is NOT the place to put your personal files in. That should be done in /home/<your log name>, where the default permissions are just right for you, and if not, you can change that.

You should understand that Unix (and Linux is a Unix clone) is the operating system (since the sixties, maybe even the late fifties) for the big main frames: giant computers, which were used by sometimes hundreds of people, often around the world, and managed by a ... manager :), who was called the root.

Every person who had a (paid or unpaid) account got his own space on the system, in /home/his_name, in which he owned the files and his personal settings, and which he could make accessible or not by a group of possibly co-workers, or class mates, or to the "world" or "others": anybody else who had access to the main frame. To prevent people from nosing into your private files, or changing these.

To be able to manage this main frame the root was all powerful: he could give you a new password, if you forget yours, to mention something. He can create standard permissions, add or delete users, just everything. He was god on the system, just as in earlier days (not now) a captain was god on his ship. He could even wreck a system, which an ordinary user can't, or the root has done something really stupid. For that he could do too.

From this resulted a standard way of organizing the disk, in /, /boot, /etc/, /bin, and so on, for the system, and a /home for the users of the system. /media and subdirectories do not fit in this system, if you use them for user files. This map (folder) is used for mounting external disks and other carriers of files, to make them accessible to users, which is different from using this folder for the user files.

I advise you to read up on Linux, and Ubuntu particularly, the more you understand the basics the more wonderful the experience is.

You could start here: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

and download, if you are lucky, the Ubuntu manual in your own language, and else in English (if E. is not your native language :) ).

It is for Ubuntu 10.10, but for the basics you can read even a manual for any other distribution, or even for Unix: it is all the same.

Howgh :)

Topsiho

---

