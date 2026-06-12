---
title: "HDD alignment and permissions Woes..."
date: 2012-01-27
forum: General Help
---

### Post by fordman1090 on 2012-01-27
Howdy,

Some of the things i may have done over the course of the past few days were without doubt not the smartest things iv ever done and they may not be good practice. But please bear with me and throw in any suggestions you may have.

Im running ubuntu 11.10 and i just updated to the 3.0.0.15 kernel yesterday i believe. I have 3 HDD's. 1x200GB that has 3 primary partitions with the 3 OS's on it and 2x2TB NTFS Storage drives.

The problems all started a few days ago as i was trying to perfect the grub triple boot into Ubuntu, windows xp and windows 7. Iv been moving around different OS files trying to get rid of the nested windows 7 boot loader. In the process of doing that I hid the 2 storage drives from windows by changing the file system to a non windows recognized file system. But something went wrong and i lost the partition on one of the storage drives. The other storage drive was already empty and i was easily able to recover the data with testdisk and copy to the alternate drive. I formatted the storage drive and re partitioned it using disk utility, but i am continually getting the warning: the partition is miss aligned by 512 bytes message. I wrote 0's to the entire drive with dd and partitioned through the terminal using parted and placing the beginning of the partition at 1MB. That got rid of the warning by left the drive as unknown. I repartitioned to ntfs using the disk utility and decided to ignore the errors. I was able to read and write to both disks last night but i am now unable to write to any of the storage partitions on either disk. When i attempt to change permissions it gives me the error "could not change permissions of "disk": error setting permissions: Read-only file system. Iv tried writing a new MBR, iv tried other file systems. But they end up being "unknown". The drives smart stat's check out fine and i haven't had any issues with it before.

Any idea of whats going on here? Could it be an issue caused by the kernel update? Iv spent far to much time searching the web for solutions, so im hoping that maybe someone can shed some light on what the issue may be. 

Thanks for any suggestions

---

### Post by WasMeHere on 2012-01-27
Hi fordman1090,

Since you have serious problems with your NTFS drives, I think you should use the tools of the original OS, Windows, to repair them. Use the disk tools you can start via the control Panel.

At least that is what I would try first, if I were in your situation.

Good luck
Olle

---

### Post by oldfred on 2012-01-27
I have never used Disk Utility for partitioning. Is that were the occasional error on mis-alignment is coming from? Most use gparted from the Ubuntu liveCD or download a somewhat newer version of gparted liveCD or parted magic.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

With Windows NTFS partitions you may have permission and ownship issues.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


Some food for thought on large data drives:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by fordman1090 on 2012-01-27
Thanks for the replies,

Olle- I booted windows 7 and it sees all the drives and data and doesn't report any problems with the partitions. Im currently formatting the drive to NTFS through windows to see what happens when ubuntu looks at it as a fresh format. 

The misaligned partition warning come from the disk utility, but fdisk -l reports that the partition doesn't begin on a physical sector boundary. 

oldfred- I used parted to partition it at one point and it resolved the misalignment issue but left the partition as "unknown" and unmountable. 

The properties of the disk say that i am the owner, but it doesnt give me write permission. I havent had any problems with permissions previously, and iv been using ubuntu for a couple years now. 

I like the idea of putting a small ubuntu partition on the disks, but im not sure if that would really help me. The disks are always used with this computer and i can usually keep my primary ubuntu install up and running and i have ubuntu live on a thumb drive for rescue and recovery stuff.

I would be up to switching to a different file system that is more compatible with linux. The only problem is that regardless of what i formate it to, it warns that the disk is misaligned. But at least when i was playing with it earlier today it was actually formatting the drive with XFS and ext4 it was letting me mount it. What would be a good filesystem to move too? I usually have each disk split into 2 partions. 1 data partition and 1 backup partition. The backup partitions store backups of the other disks data partition. This lets me read data from one disk, while writing data to the other so i can get through more data faster.

---

### Post by WasMeHere on 2012-01-27
> **fordman1090 said:**
> Thanks for the replies,

Olle- I booted windows 7 and it sees all the drives and data and doesn't report any problems with the partitions. Im currently formatting the drive to NTFS through windows to see what happens when ubuntu looks at it as a fresh format. 

The misaligned partition warning come from the disk utility, but fdisk -l reports that the partition doesn't begin on a physical sector boundary. 

oldfred- I used parted to partition it at one point and it resolved the misalignment issue but left the partition as "unknown" and unmountable. 

The properties of the disk say that i am the owner, but it doesnt give me write permission. I havent had any problems with permissions previously, and iv been using ubuntu for a couple years now. 

I like the idea of putting a small ubuntu partition on the disks, but im not sure if that would really help me. The disks are always used with this computer and i can usually keep my primary ubuntu install up and running and i have ubuntu live on a thumb drive for rescue and recovery stuff.

I would be up to switching to a different file system that is more compatible with linux. The only problem is that regardless of what i formate it to, it warns that the disk is misaligned. But at least when i was playing with it earlier today it was actually formatting the drive with XFS and ext4 it was letting me mount it. What would be a good filesystem to move too? I usually have each disk split into 2 partions. 1 data partition and 1 backup partition. The backup partitions store backups of the other disks data partition. This lets me read data from one disk, while writing data to the other so i can get through more data faster.

Since you are using Ubuntu, and need not reach the partitions from Windows, I suggest that you format the data and the backup partitions to ***ext3***. This will be read and written faster by Ubuntu compared to NTFS, and the linux file permission system will work properly. And I suggest that you use Gparted.

---

### Post by oldfred on 2012-01-27
Ignore the fdisk error on physical sector boundaries.  Since drives went over 8GB years ago BIOS has had to use LBA. Back then we had to key in the cylinders, heads & sectors into BIOS.

Formating stayed with what would have been sector boundries, but with new drives, SSDs they now use 1k blocks.

---

### Post by fordman1090 on 2012-01-27
Olle- Once windows finishes formatting the 2TB's, which may take a while. Ill boot back to Ubuntu and see what it says and hopefully all is well and i can format it with Gparted. 

lodfred- I had heard that the misaligned warning isnt really a problem for most drives and that it was only a few drives that use the Advanced Formate style that is affected by misaligned partitions. But what kinda has me confused is why did it just start doing it so randomly. I hadn't ever had that problem with this before. But if its not an issue, im not to worried. Maybe using Gparted will get rid of it. 

Is ext3 the best/fastest file system to use? or would ext4 or xfs be better?

---

### Post by WasMeHere on 2012-01-27
> **fordman1090 said:**
> Olle- Once windows finishes formatting the 2TB's, which may take a while. Ill boot back to Ubuntu and see what it says and hopefully all is well and i can format it with Gparted. 

lodfred- I had heard that the misaligned warning isnt really a problem for most drives and that it was only a few drives that use the Advanced Formate style that is affected by misaligned partitions. But what kinda has me confused is why did it just start doing it so randomly. I hadn't ever had that problem with this before. But if its not an issue, im not to worried. Maybe using Gparted will get rid of it. 

Is ext3 the best/fastest file system to use? or would ext4 or xfs be better?
I suggest ext3 because it is very well proven, not quite as fast as ext4, but there is more data buffering with ext4, which can cause problems at power failures. I have no experience of xfs.

---

### Post by fordman1090 on 2012-01-28
Ok, so windows finally finished and as i suspected, i still got the misalignment error. So i loaded GParted and used it to create the new partitions. It worked like a charm. But I cannot seem to get the permissions to allow me to write to any of the non system partitions. Iv tried NTFS and ext3. NTFS at least says that im the owner, but restricts me to only accessing the files. The ext3 partition gives ownership to root and displays the drive as "1TB File System" in the file browser. I played with the fstab and the wr, user options a little, but it showed both the fstab mount icons and the actual hdd partition icons in the device menu, and when you selected the fstab mount icon it would fail.

This is the first time i have had this much of a problem with permissions.There is one user on the machine and that is me. It makes me wish that i could tell the computer that im the freaken root user and let me do what i want!!!!!! There just isnt a reason for running into these problems with permissions and I guess i just kinda feel like im chasing ghosts and its getting annoying.

Thanks for all the help so far, im really hoping to get this sorted out as im already having projects stack up.

---

### Post by WasMeHere on 2012-01-28
How do you mount the files?

Linux files have their permissions that you can set and reset individually with chmod (or properties in Nautilus). Can you mount it from Nautilus or do you mount it with mount in a terminal window?

Windows partitions (NTFS) have their permissions set and reset when it is mounted (at least you run them from Linux). So you should mount them with read + write permissions. This is often done automatically via Nautilus, when you click on it in Nautilus.

---

### Post by oldfred on 2012-01-28
If it is a fixed drive you should mount it with fstab so you have total control over ownership & permissions.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by fordman1090 on 2012-01-28
Thanks oldfred for the links, they were quite helpful,

Iv been using Nautilus to mount it and it would mount the ext4 with the owner as root and the ntfs with me as the owner but access only permissions. 

I eneded up changing the file permissions of the /media/data and /media/backup to rw for everyone using $sudo chmod 777 -R /media data and @sudo chmod 777/ -R /media/backup. Then i changed the owner to me using sudo chown for each file. This has seemed to work so far and it stuck through a reboot. 

Im gonna play with the fstab a little to see if i can get it to mount them on start up without any issues.

after a little research Iv decided to use ext4 for the improvement in speed and i can still access it from windows if i need. I figure that the system is stable and on a battery back-up and about 90% of the data i write isnt important, so the chances of losing truly important data is rather small.

The filesystem reports about 50GB as used when the disk is empty. Is that normal with the ext filesystem?

Thanks again to both of yall for all the help.

---

### Post by WasMeHere on 2012-01-28
> **fordman1090 said:**
> Thanks oldfred for the links, they were quite helpful,

Iv been using Nautilus to mount it and it would mount the ext4 with the owner as root and the ntfs with me as the owner but access only permissions. 

I eneded up changing the file permissions of the /media/data and /media/backup to rw for everyone using $sudo chmod 777 -R /media data and @sudo chmod 777/ -R /media/backup. Then i changed the owner to me using sudo chown for each file. This has seemed to work so far and it stuck through a reboot. 

Im gonna play with the fstab a little to see if i can get it to mount them on start up without any issues.

after a little research [COLOR="Red"]Iv decided to use ext4 for the improvement in speed and i can still access it from windows if i need.[/COLOR] I figure that the system is stable and on a battery back-up and about 90% of the data i write isnt important, so the chances of losing truly important data is rather small.

The filesystem reports [COLOR="Red"]about 50GB as used when the disk is empty[/COLOR]. Is that normal with the ext filesystem?

Thanks again to both of yall for all the help.
I'm glad you have made progress with the file permissions. Good luck with fstab!

Now to the red text: I don't think Windows can read (or should we say wants to read ext4 partitions). And no, 50 GB is hiding somewhere. Maybe you have deleted files, that are lurking in linux or windows trashcans?

Files and directories starting with dot . are hidden in linux. you can see them with
```
ls -la
``` 'list long all'

---

### Post by oldfred on 2012-01-28
Is it space used or the difference in GiB and GB that you seem to have Gb's missing?

Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)

Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by fordman1090 on 2012-01-28
It reports 50GB as being used. From what iv read in the links posted by oldfred, ext3 & ext4 reverse about 5% of the disk capacity for root use. This is space that is set aside so that the OS can still operate if the disk becomes full. So, my partition is 1000GB x 5%(0.05) = 50 GB.

But just to check i ran ls -las and got back ".", ".." and "lost + found". All of it only takes up about 24 blocks which is only 96KiB, if the 4KiB block size i found is correct.

This can be disabled when the drives are formated, so i may try that to see if it frees up that extra 50GB's. Its not a system drive so it shouldn't need any reserved space.

Yet again, i am tremendously thankful for yall help.

---

### Post by fordman1090 on 2012-01-28
Actually, i decided im not gonna mess with getting ride of the reserved space. If it becomes an issue later ill deal with it, but i dont think it will be a problem.

---

### Post by WasMeHere on 2012-01-28
> **fordman1090 said:**
> Actually, i decided im not gonna mess with getting ride of the reserved space. If it becomes an issue later ill deal with it, but i dont think it will be a problem.

Think twice before doing it! The file system ext2 is simpler, ext3 and ext4 has journaling, that uses spaces. And if there will be problems, the information in the journals is very valuable.

---

