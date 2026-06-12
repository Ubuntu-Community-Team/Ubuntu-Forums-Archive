---
title: "Lost data"
date: 2011-10-25
forum: General Help
---

### Post by Total Noob on 2011-10-25
I bought external memory, a Hitachi Lifestudio formatted with msdos, and was fooling with my files using Ubuntu 10.4 when suddenly the external memory seemed to drop off as if it had been physically disconnected. 

When I unplugged/replugged it, 9 gigabytes worth of work files involving hundreds of hours of effort were not to be found. The top level folder remained, but no underfolders and no files. I did not trash them; to do that, I would have had to move 10 main underfolders to trash and I didn't do that, and it takes time for them to go, and there was no waiting. Just gone.

I tried to recover them using the Windows program Recusa, which did not see the files though they seem to be there (checking properties). I tried the Linux programs Mondo and Magicrescue, but while these installed from the repository, I could not find them on any menu.

Can these be recovered? Where could the files have evaporated to? Thanks.

---

### Post by cryptotheslow on 2011-10-25
What do you mean by "they seem to be there (checking properties)"?

Whatever you do - do not write any other files to the drive until you have (hopefully) recovered what appears lost.

When booted into Ubuntu (rather than Windows) - with the drive connected, open a Terminal and execute these two commands and post back the output here:

```
   mount

    fdisk -l

```

That is a lowercase L on the fdisk command - do not use any other option.

The first command lists all filesystems that are currently mounted.
The second command lists the partition table for all disks.

This information will help people with subsequent commands to try to help you.

---

### Post by Total Noob on 2011-10-25
> **cryptotheslow said:**
> What do you mean by "they seem to be there (checking properties)"?

Whatever you do - do not write any other files to the drive until you have (hopefully) recovered what appears lost.

When booted into Ubuntu (rather than Windows) - with the drive connected, open a Terminal and execute these two commands and post back the output here:

```
   mount

    fdisk -l

```

That is a lowercase L on the fdisk command - do not use any other option.

The first command lists all filesystems that are currently mounted.
The second command lists the partition table for all disks.

This information will help people with subsequent commands to try to help you.

I did it and this is what I got. Is it any help? Note: Lifestudio is the name of the external drive from the manufacturer, Hitachi. Thanks.

```
no@no-Aspire-3620:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/no/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=no)
/dev/sdb1 on /media/LIFESTUDIO type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
no@no-Aspire-3620:~$ fdisk -l
no@no-Aspire-3620:~$ 




```

---

### Post by cryptotheslow on 2011-10-25
Sorry - that 2nd command should have been:

```
 sudo fdisk -l 
``` (that's a lowercase L)

And - What do you mean by "they seem to be there (checking properties)"?

---

### Post by Total Noob on 2011-10-26
> **cryptotheslow said:**
> Sorry - that 2nd command should have been:

```
 sudo fdisk -l 
``` (that's a lowercase L)

And - What do you mean by "they seem to be there (checking properties)"?

I thought I knew how many files and what space should have remained on the Lifestudio drive based on what I moved there a few days before, which is when I bought it new. When I checked properties for the whole drive, the right number of files and space seemed to be there, as if nothing had been deleted, but the master folder for that work was listed as empty. I assumed the files went to some kind of holding area, maybe root trash or something, but I don't have the skills to find it.

Just now, I checked properties for the whole drive, and found contents totaling 48.8 GB and used totaling 59.3 GB, with the 10.5 GB disparity being just about exactly what disappeared on me.

In any event, I lucked out by being able to recover about 98% of my data from the prior storage drive with Pandora for Windows, which is painless and quite good.

However, I lost tree structure and file names; I lost about 2% of my files outright, either through inability of Pandora to recover them or failure to know where they were before I put them on my Lifestudio; and I had about 50 corrupted photos that won't launch under the usual programs, gimp, paint, photoscape.

Does anyone know how to get the original tree structure and file names back for recovered files, and the name of software that will open corrupt photos and save them uncorrupted?

Thanks.

---

### Post by oldfred on 2011-10-26
Were any of these files over 4GB in size? FAT32 has a hard max of 4GB file size and corrupts any file over 4GB - those will never be recoverable. FAT also does not have a journal so it is hard to run chkdsk to repair. Better to use NTFS is you have to have Windows compatibility, but you still need to run chkdsk every 30 or 40 boots to make sure it is ok.

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

---

### Post by Total Noob on 2011-10-26
> **oldfred said:**
> Were any of these files over 4GB in size?  

No. Most were < 1 mb, some got up to 12 or so mb, nothing anywhere remotely near a Gb.

> **oldfred said:**
> Better to use NTFS is you have to have Windows compatibility, but you still need to run chkdsk every 30 or 40 boots to make sure it is ok.

How do I do that? Is that the disk checking that gets done if Windows crashes and I have to unplug the computer?

---

### Post by Nixarter on 2011-10-26
I strongly suggest that you either 1.  do not use chkdsk, or 2.  do a full (byte-by-byte) backup of any drive before you use that program.

It is notorious for corrupting drives and files, and make recovery an absolute pain, if not impossible for many files.  And that's for normal, healthy partitions.  If there is missing/lost/deleted data on the drive and then you run it, it and/or defrag have a very good chance to scramble random parts of files to make them unrecoverable.

On any drive that has any missing data, the first step is to use a program like dd to image the drive, then work on the image, not the drive.  That way, if you try something risky (which could be anything at all, esp if the drive is failing), you have the best possible copy of the drive, with no chance to screw up the original.  Then run whatever you like-- just don't touch the original.

---

