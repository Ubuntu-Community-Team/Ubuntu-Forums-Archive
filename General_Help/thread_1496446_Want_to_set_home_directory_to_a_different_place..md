---
title: "Want to set home directory to a different place."
date: 2010-05-29
forum: General Help
---

### Post by irv on 2010-05-29
I'm looking for a little direction.
I have a Laptop running Win7 and Ubuntu 10.04 Here is a what my gparted looks like:
[ATTACH]158646[/ATTACH]
I want to first boot with the Live CD and grab a 30 gig slice of the hard drive and format it fat32. Then I want to set it up to my home directory, but I know if I do this my Ubuntu will come up with error when I boot. I know because I did this one time before a few years ago.
So my question is, How do I set it for home without getting errors? Is there a howto out here telling how to do this? Do I need to do it from within Ubuntu or the live CD? I have everything running as I want, and I want to keep it that way.
One other thing: Would I be better off leaving the home directory alone and just using the 30 gig slice to use with Win7 and Ubuntu?
Just want to do it right.
Thank for the help ahead of time.

---

### Post by irv on 2010-05-29
So far what I have done is shrink /dev/sda2 and /dev/sda5 with gparted. Then I created two fat32 partitions, /dev/sda4 and /dev/sda7. I wanted to combine them into one partitions, but I couldn't figure out how to do it. I could resize them, but I couldn't move them. I tried copy and past, but all that does is copy sector data from one to the other. Before I try to make this my home directory I would like to combine them. Here is a screen shot of my gparted layout now with the changes.
[ATTACH]158662[/ATTACH]
By the way everything is still working. (Windows and Ubuntu) The next things I do are critical. So I do need some help. I have found some help on line, but I am walking careful.

---

### Post by oldfred on 2010-05-29
Ubuntu's home has to be a linux partition to support ownership and permissions which windows partitions of FAT or NTFS do not support. So no you cannot make a FAT partition home.

That said you can make data partition(s) and data in FAT or NTFS can easily be shared. Permissions and ownership are set at time of mounting. Kinda a default as they do not support them.

I would rethink FAT partitions. Only use them when you have to like for flash cards used in cameras etc. FAT will not store files over 4GB and will not give an error when you copy a file over 4gb, just destroy it. FAT also does not have journaling, NTFS does so you may be able to recover data from NTFS where with FAT it is less likely. Some older links may show FAT as a choice because several years ago the NTFS driver in linux was not 100% reliable. It is very reliable now.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by irv on 2010-05-29
Oldfred, this is some great stuff, and I will check out all the links you gave and re-think which way to go.
Thank for the tips.

---

### Post by irv on 2010-05-29
OK, here's what I decided to do. I set /dev/sda4 to ntfs and put the files from My Document directory in there to share with Ubuntu. Then I set /dev/sda7 to ext4, and I am going to use it for moving files from my /home directory if I ever do a fresh install of a Linux OS so I can just pull my files over to the new install.
I also do a complete backup of my files to a USB 1terabyte drive for safe keeping. So here is the final screen shot of gparted.
[ATTACH]158704[/ATTACH]

---

### Post by oldfred on 2010-05-29
What ever works for you. I found every year or so I wanted something different but did not really change until I bought the new larger drive.

I mounted my shared NTFS drive in /home as /home/fred/shared. I also put pictures, firefox profiles & thunderbird profiles in the shared so I have the same settings in both. It made it easier for me to get the spouse to convert as she barely new the difference. The main complaint then became solitaire was different. 
I never saved anything to my documents and some programs in windows want to save to the program directory. So I created a .bat file just to make sure all the files I cared about could be copied to the shared partition.

---

