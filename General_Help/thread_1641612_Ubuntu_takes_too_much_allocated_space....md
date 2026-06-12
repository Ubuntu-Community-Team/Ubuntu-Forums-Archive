---
title: "Ubuntu takes too much allocated space..."
date: 2010-12-09
forum: General Help
---

### Post by flagstar on 2010-12-09
This occur when I used Ubuntu for over 6 month now.

When I install UNR 10.04 dual-boot with WinXP on eeepc netbook and allocated with 16GB for Ubuntu itself and once install, I got 14GB and more free space and I think it was good enough...

After about 4-6 month, Ubuntu start to clog, slower respond time and takes very much free space. Now I have about 5.4GB left while I only use about 5-6GB on home folder. And I got issue with Firefox keep hang when loading a certain page whereas it did not happen before... I try with clearing cache but it did not help free up space.

Is it because of frequent update from Update Manager or I just used wrong software? Can anyone help? Thanks in advance...

---

### Post by drs305 on 2010-12-09
If you don't know where your free disk space has gone you can go through this guide on disk space. It provides commands and tools to help identify large files, undeleted trash which still takes up drive space, etc.

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by flagstar on 2010-12-14
~$ df -Th | grep -v "fs" | sort 
/dev/loop0    ext4     16G  8.7G  5.8G  61% /

it show that I used 8.7G on 16G partition but in Home Folder it was only 4.5G. I did not done any backup either and the partition works fine but the performance was slower than the 1st installation of LTS...

result for 'apt' are as follow

~$ du -h /var/cache/apt
456K    /var/cache/apt/archives/partial
199M    /var/cache/apt/archives
228M    /var/cache/apt

Can anyone help me?

---

### Post by drs305 on 2010-12-14
You can clean out your downloaded packages (which aren't really needed) by running the following command:
```
sudo apt-get clean
```

This will free up some space (from /var/cache/apt).

You might do the 'large file' search command from the Disk Space link I provided earlier to see if you have a few large files you don't need, and also make sure to check your Trash bin and root's Trash bin. Even though deleted, these files take up space until permanently removed from the Trash bin.

---

### Post by logan_2k6 on 2010-12-14
happens the same to me too...
BUT I USE WUBI INSTALL WITH 20 GB "HARD DRIVE"

didn't restart my computer in a few days....and somehow just 10 min ago i manage to get 0k space on my ubuntu disk.

space was getint lower and lower by the day/min/whatever....at first i thought maybe i have some downloads in dc++...but my home folder had only 5 Gb....but still my space was getitn smaller and smaller until i finally manage to get 0 bytes free disk space.

So....what i have done was restarting in windows and chkdsk on the drive that i have ubuntu.

After that restart back in ubuntu...seems that i have 7.8 Gb FREE now....MAGIC :D

---

### Post by flagstar on 2010-12-15
I did the clean up for unused packages and trash which only free up lesser than I expected. When I browse the FileSystem file exclule Lost+Found and Root, I found out the culprit was in this directory

FileSystem/Proc which takes 1G
FileSystem/Usr/lib took 1G
FileSystem/Usr/Share also took 1G
and various files which accumulate to more than 1G

can I clean this file out or it is necessary for Ubuntu to run?

---

### Post by mcduck on 2010-12-15
*/proc* is a virtual filesystem, and doesn't exist on your hard drive. So it's not using any of your disk space.

*/usr/lib* and */usr/share* are pretty much where most of the files for your programs are installed. 1GB of size seems quite reasonable for both, assuming you aren't running some kind of minimal install with only a few (or very lightweight) applications installed.

What I'd recommend is checking your home (including hidden files!) and root user's trash (/root/.local/share/Trash). Also check */var/log*, where all the log files are located. If your drive space is disappearing quickly you might have some problem on your system, resulting in lots of error messages in some log file and thus growing the logs to huge sizes.

And of course make sure you haven't enabled some kind of backup tool at some point. I've seen quite many people on these forums with a similar problem, just to find out that they had enabled Simple Backup and forgotten about it, and the backups were taking all the space.

edit: If you don't know for sure what some file or directory is (and it's not located inside your home directory) you definitely should leave it alone. Or at least ask on these forums before deleting it.

---

### Post by logan_2k6 on 2010-12-15
is it possible that some of these "virtual drives" like /proc and whatever to actually take space from hard drive?

Im pretty much sure that the restart solve the problem for me...i am just afraid to not lost my space again.

7.8 Gb after a restart is a lot of space...
My system couldnt start almost anything (even that console window show me an error)...firefox couldnt show web pages right (it was already open when i had 0 bytes free)....
The only other program that was running (other than firefox) was Banshee....this one was palying music from a radio station....
so i really have no idea why my space was gone....but after restart my space was back.


Edit: i think i lost 600 Mb again somehow

---

### Post by drs305 on 2010-12-15
> **logan_2k6 said:**
> Edit: i think i lost 600 Mb again somehow

Check for large log files in /var/log or backups being made to the wrong mount point (being put in your system partition instead of another partition - a favorite of sbackup).

Here's a guide on finding out what's taking the space:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by logan_2k6 on 2010-12-15
ah it seems that i forgot to move 1 download...guess my space is ok... for now

---

### Post by flagstar on 2010-12-16
I've check /var/log and it did not accumulate to more than 10M so I think it's fine... 
Both Root and Lost+found folder shows nothing using 'gksudo nautilus' command. 
Even Trash folder are completely empty. 
Current Home Folder now used 4.8G the last time I checked which leaving free space to 5.5G.

I've been wondering where's the rest of free space left about 3-4G missing since I allocated 16G for Ubuntu using Wubi...

---

