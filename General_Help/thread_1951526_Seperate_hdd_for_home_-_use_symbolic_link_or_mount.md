---
title: "Seperate hdd for /home - use symbolic link or mount?"
date: 2012-04-02
forum: General Help
---

### Post by mashedbear on 2012-04-02
Hi 
after a failure of my primary hdd, I am about to install an 60GB SSD to run Ubuntu OS and will use a separate hard drive for /home - ie all the user data. 

The hdd I will use was my back up hdd and has /home and all the data for 5 users already on it (this hdd was previously mounted under /mnt and I rsync'ed /home from the primary hdd to this hdd nightly).  

My question I have is when I install Ubuntu on the 60GB SSD what is the best way to have /home on a separate hdd? 

I can see two options: 

1) Mount the second drive as /home - perhaps in a similar way to this: 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

or:

2) Mount the hdd under /mnt and create a symbolic link from /home on the SSD to /home on the hdd. 

The second option sounds easier. Would this work? What would the drawbacks be? Is there a better way?

Also how do I deal with user permissions. If when I reinstall Ubuntu I use the same user names and system privileges as before will everything 'magically' just work for the existing user data on the separate hdd?

Finally the hdd is an ext3 file system. I am planning to format the SSD as ext 4. Will this work as either symbolic link or mount solution? Or do I need to format the SSD as ext3? 

I've not had to do a rebuild like this before, and don't have much experience of mount points or symbolic links, so thanks for any help and advice.

---

### Post by oldfred on 2012-04-02
I do not think you can symlink /home but you can do that for all the folders in /home if you want. If you use same user UID 1000 )default first user), your old /home if mounted as part of the install will just become your new /home. It should not create any problems at all, but if you boot your old system the new settings for the new software may not be compatible.

I have posted several times on separating /home into settings which I keep on my SSD (and my installs on hard drive) and data which I have on several drives and symlink into my /home.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

For my 60GB SSD, I create two 30GB / (root) partitions and plan to have 12.04 as my working install and another install in the other partition. My wife now does not let me update every 6 months like I would so I will probably stay with 12.04 for a while, but I still install the new version to try it out.

I used gpt partitioning which is the newer update to MBR partitioning. But I hope to get a new UEFI system this year so I left a partition at the start for the efi partition, but with BIOS need the bios_grub partition. 

```
fred@fred-MavericDT:~$ sudo parted /dev/sde unit s print
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name  Flags
 1      2048s      616447s     614400s    fat32              boot
 2      616448s    618495s     2048s                         bios_grub
 3      618496s    58925055s   58306560s  ext4         04
 4      58925056s  117229567s  58304512s  ext4         10


```My SSD is a Microcenter house brand. You may want to review this:
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by mashedbear on 2012-04-03
Thanks oldfred - working through your advice and the links, and am about to make a start on installing. Will update the post with how I get on.

One question should /swap NOT be on an SSD? Is it best this partition is on an HDD. does this matter on 'new' SSDs?

---

### Post by jerome1232 on 2012-04-03
> **mashedbear said:**
> 
One question should /swap NOT be on an SSD? Is it best this partition is on an HDD. does this matter on 'new' SSDs?

If it's going to be on an ssd, make it a swapfile to take advantage of TRIM.

---

### Post by mashedbear on 2012-04-03
Making progress - I think... see below..   not sure if the Extended partition is expected.. but sda5 is for /home and /sda6 is swap - again not sure if this was the best idea but we learn as we go right? 

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009eda3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    58593279    29295616   83  Linux
/dev/sda2        58595326    85981183    13692929    5  Extended
/dev/sda5        58595328    78168063     9786368   83  Linux
/dev/sda6        78170112    85981183     3905536   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035508

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux


Now looking into moving the mount point for sdb1 from /media where it has defaulted to /mnt where I think it should be. Is this just good housekeeping .. I could just leave it where it is!

thanks for help so far.

---

### Post by oldfred on 2012-04-03
You see a lot of discussion on where to mount drives. Some say /media is for temporary mounts, others claim it is for all mounts.

For me the decision is do you want to see it in the left panel of Nautilus or not. 

If you want it in the left panel use /media or /home as a mount.

I do not, since I have symlinked all the folders into /home and it is redundant. So I use /mnt which will not be in the left panel. But I sometime have to drill down from system if I want to see the folders as they are in the drive not as they are symlinked.

---

### Post by mashedbear on 2012-04-03
Thanks. Got it. sdb1 now mounted to /mnt/data

Now to symlink /home/me to /mnt/data/.../me

Not sure how to do this yet - but getting there!

---

### Post by oldfred on 2012-04-03
It is the other way around. You symlink the folders in /mnt/data into /home

From your /home.

#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music

I am up to 13 or 14 folders in my /data and doing the above for each was too much. Then I found this little script that links them all at once. If the name is the same you have to have renamed or deleted from /home like I show above with Music. I do this as part of a new install, so I know all the default folders are empty so I just delete them, not rename.

#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by mashedbear on 2012-04-03
Thanks. Got it. Music now linked manualy. Will think if I can link everyting using your script - or maybe thinking will just leave music video and photos on sdb1 (ie /mnt/data) and move docs and stuff on to the ssd and leave them there. 

I use rsync to back up to an external drive. Will rsync follow symlinks? or is there a flag I need to set?

Probably heading to bed now and pick up on this again tomorrow night. 

Thanks again for your help - I really appreciate it.

---

### Post by oldfred on 2012-04-03
I do not use symlink in my rsync scripts, just the mount /mnt/data/Documents for example.

I think that can be an issue and with some networking the use of bind instead of symlinking is preferred.

---

### Post by mashedbear on 2012-04-06
OK. Thanks - tested script works great. 

Have made a backup of mnt/data using rsync to an external hard drive; checked this with diff and we are good.

Understand how to re-create the users in the right order, so I can keep permissions. 

Experienced a few issues in some tests with symlinks as the data on my existing hdd (which was a back up of the failed drive) had a /home folder. This seemed to confuse quite a few things. Have reorganised this so there is no /home on mnt/data, and this seems to work better.

Access times from the SSD and HDD are very close so for ease I think all data will live on the HDD ie /mnt/data

Now working on how to recover my shotwell database - prefer not to loose all tags etc. Can see where the shotwell db is in ~/.shotwell in my backups. Now researching how to use this in the new setup - as the paths to the jpgs will have changed. Possibley need some SQL to change all the paths in the SQLlite db... 

Anyone have any documentation / ideas on this?

---

### Post by mashedbear on 2012-04-10
OK. Sorted I think, and closing the thread as solved.

I used SQLlite to look at the paths for the media in both shotwell and banshee-1 and looked into the hidden dir where the dbs live, thumbs etc live in .shotwell and .config/banshee-1. 

Worked out both apps would follow the symlink in my new /home to /Pictures and /Music on mnt/data and that I could also symlink from /home/.shotwell and /home/.congfig/banshee-l to the dbs and thumbs on /mnt/data which makes it easy to backup shotwell and banshee dbs.

Thanks to oldfred for his help.

---

### Post by oldfred on 2012-04-10
Glad I could help. :)

---

