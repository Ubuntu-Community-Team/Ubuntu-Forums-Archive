---
title: "stretch my partition - how ?"
date: 2011-01-28
forum: General Help
---

### Post by ThaDoctor99 on 2011-01-28
Hi 

I got some strange problem.
I installed ubuntu and thought that were all fine (and it was)
but now it begin to tell me I only got about 60 GB in my home folder (I got a 320GB disk in - it is only a laptop)
now I would just like to get some idea about how I can stretch my home partition. 
When I looked at my disk with "du" it did only tell me my home used about 56GB or something like that
I am running 10.10 64 bit
and I run Vuze a lot of time.
What could be my problem, if you guys need more info just ask.

Greetings Denmark

---

### Post by Mark Phelps on 2011-01-28
> **ThaDoctor99 said:**
> ... if you guys need more info just ask.

OK ... then open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions in your system.  Need to see those details before we can give you detailed advice.

---

### Post by ThaDoctor99 on 2011-01-28
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062949

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   601368575   300683264   83  Linux
/dev/sda2       601370622   625141759    11885569    5  Extended
/dev/sda5       601370624   625141759    11885568   82  Linux swap / Solaris
#_________________________________________________________________________
#below is the external drives :D
#_________________________________________________________________________
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x530906b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92590e09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001    c  W95 FAT32 (LBA)

---

### Post by ThaDoctor99 on 2011-01-28
There is also another thing, everytime I try to free up some space from deleting files, its only free for a second as it then tells me that there is only 4 kb free even if I just deleted 6GB

---

### Post by oldfred on 2011-01-28
Do you have a runaway process that is recording lots of data to a log file? I would check top to see what is running and check log files that may be growing too large and recording many errors.
HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by ThaDoctor99 on 2011-01-28
I did all of those apt-get tricks without anything to show for it.
Still the same problem, except I can update programs even though it says there is no space on device. - It also complain about my 1TB harddisk is full even though there is only 570GB on it.

---

### Post by oldfred on 2011-01-28
What does this show?
 
df -H 

and:

sudo du -hc --max-depth=1

---

### Post by ThaDoctor99 on 2011-01-28
Strangely enough a reboot solved the problem, I got tired enough of it to reboot. 
However I still have no idea what was wrong... Well Thanks for the help.
mv df -H showed 18% use on /

---

