---
title: "New Install Won't Boot"
date: 2012-01-20
forum: General Help
---

### Post by caned_monkey on 2012-01-20
Hello,

I've tried a lot of searching on this but I cant find anything that matches my problem.

I'm trying a fresh install of Ubuntu alongside XP, same HDD, same partition as XP. The install goes OK but when I reboot I'm getting the message:

error: no such device 0E2C1622B2C160DF9
error: no such partition

press any to continue...

I press a key nothing happens.

I've had Ubuntu on my machine before and it worked fine but i recently formatted my hard drive, reinstalled XP and added a second HDD. Now I cant get Ubuntu to boot.

Thanks in advance

---

### Post by mörgæs on 2012-01-21
Hi, welcome to the fora.

Since this is not specific to Dell I have moved your post.

---

### Post by caned_monkey on 2012-01-22
bump ;)

---

### Post by oldfred on 2012-01-22
Post boot info scripts results.txt to see your entire configuration. Boot repair can run script and often can make repairs.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

---

### Post by caned_monkey on 2012-01-23
OK thanks, I used the boot repair CD and here's the url:

[http://paste.ubuntu.com/814722/](http://paste.ubuntu.com/814722/)

---

### Post by caned_monkey on 2012-01-23
deleted

---

### Post by oldfred on 2012-01-23
You can just delete text. I do not know if it is because you used Windows with its different line endings or what but it is unreadable. 

The link works fine & has good formatting.

It looks like you have several installs of wubi. Wubi is intended for Windows users who are not sure they want Ubuntu and can easily install/uninstall inside the Windows NTFS partition. It is a longer test than a liveCD and is update-able but not for long term use.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


You have two 1TB drives and Ubuntu only needs about 20GB for a full install to a separate partition. If you really want to try Ubuntu you may want a full install.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

### Post by caned_monkey on 2012-01-23
OK I understand. I didnt realise that the windows installer wasnt the full install. the reason I have more than one installed is because i tried installing it to different partitions when the first one failed. I thought i had uninstalled it each time so, the question is, how do i get rid of it if the uninstall.exe dosent do the job?

---

### Post by oldfred on 2012-01-23
the wubi guide has manual uninstall instructions. With XP you delete the entry in boot.ini and just delete the wubi files.

[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

I do not know how much space you want to allocate to Ubuntu. But with the large drives you should have room.

I like to keep a different operating system on every drive. I have Ubuntu on every drive but my old XP which I rarely boot anymore.

I liked the logic this used.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by caned_monkey on 2012-01-24
Thanks for the help Oldfred.

Just out of interest, why would you need a different OS on each drive, how many drives do you have?

I got my second hard drive because my old hard drive died not that long ago and I came within a whisker of losing everything. This really scared me so I got two hard drives to replace it. I have them partitioned like this:

C: 150GB for my Windows system on first HDD
F: 780GB for Storage on first HDD
G: 150GB for program files on second HDD
H: 780GB space to backup storage on second HDD

I was going to put Ubuntu on the C: partition which is what i was trying to do with wubi (thats why i allocated so much space so there was more than enough room for both), but am i right in thinking that a full install requires its own dedicated partition? Whats the advantage to having it on it owns HDD?

---

### Post by oldfred on 2012-01-24
When I built my system 6 years ago I added two 160GB drives. Then to add space a couple of years ago I added a 640GB drive. And just to speed some things up I just added a small 60GB SSD. 

So 4 drives, but my 640 has 2 100GB data partitions, one NTFS from when I still had XP running and one ext3. I am then just adding 25GB / partitions for installs. Many are obsolete, some are just for a test, but I think I can boot them in case I want to test something.

---

### Post by cbanakis on 2012-01-24
I have had a problem with booting that might be related.  (long shot though)

For some reason, if you have multiple hard drives in one system, Ubuntu  likes to install the boot loader on the lowest numerical device,  regardless of what drive Ubuntu itself is installed on.

So if you install Ubuntu on disk 2, and tell the BIOS to boot to disk 2, it wont work.
Because the boot loader was installed on disk 1.

See thread [http://ubuntuforums.org/showthread.php?p=11626586#post11626586](http://ubuntuforums.org/showthread.php?p=11626586#post11626586) for more details, if this sounds like it could be your problem.

---

### Post by cbanakis on 2012-01-24
Deleted

---

