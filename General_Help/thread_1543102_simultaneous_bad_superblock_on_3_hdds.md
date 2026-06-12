---
title: "simultaneous bad superblock on 3 hdds"
date: 2010-07-31
forum: General Help
---

### Post by pharcycle on 2010-07-31
dear all,

I had been running mythbuntu 10.04 x64 quite well until the other day when i noticed that a couple of my partitions weren't available. I ran sudo mount -a and it failed so i reset. During the boot process it reported an error and gave me the option to hit 'S' to skip or 'M' for manual repair. I'm not too hot on command line tools so i couldn't do much in the prompt and rebooted into a live cd (ubuntu 10.04 x64). 

If i try to open a damaged partition i get an error 

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```doing what it suggest:

```
ubuntu@ubuntu:/$ dmesg | tail
[19648.660816]   domain 1: span 0-7 level MC
[19648.660818]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[19648.660826] CPU7 attaching sched-domain:
[19648.660828]  domain 0: span 3,7 level SIBLING
[19648.660830]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[19648.660835]   domain 1: span 0-7 level MC
[19648.660837]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[19770.744989] JFS: nTxBlock = 8192, nTxLock = 65536
[24595.405485] jfs_extendfs: volume hasn't grown, returning
[24628.371768] jfs_extendfs: volume hasn't grown, returning
```
if i open gparted and run 'check' from the menu on the partition, it completes successfully and i can now open the partition fine and see the data. Upon reboot i still get the same error if i try to boot mythbuntu and again the live cd can't see the partitions without me running gparted first.

The partitions that have failed are on 3 physical hdd's, 2 used for mythtv recordings and one for my archive folder, the others 2 drives in my system are still working fine.

I've attached the gparted output (it was originally a .htm but had to rename it to .txt to upload).

can anyone help shed some light as to whats happening?

the last thing i was working on before it stopped working was installing im-sensors to monitor temps and trying to get rhythmbox play mp3's.

EDIT: the affected partitions are all jfs partitions. I run xbmc a lot as well as mythtv.

Many thanks.
David

---

### Post by gzarkadas on 2010-08-01
The gparted check-log you attached reports only /dev/sdc1 and /dev/sdd7._   I haven't ever used jfs_, but the way to proceed in such issues is to first identify the faulty drives, then see what errors they output and then try to run the appropriate tools (in this case jfs_fsck)  to correct them. Please post here:

[LIST]
[*]Your /etc/fstab, to see the drives/partitions that are in error.
[/LIST]

[LIST]
[*] A selection of your syslog (file /var/log/syslog) showing the hard disk errors of the last boot process. You will have to make this selection yourself but its not that hard.
[/LIST]
[INDENT] If you use a GUI desktop, open the Log Viewer application, go to the `syslog' item in the list at the left and then scroll the window at the right down to the end. Then go upwards until you find early boot messages such as "Booting processor...", "Initializing CPU...", etc. Select everything from this line to the end, then copy and paste it to an editor window, then save it as a file.

If you use the command line, do a ```
sudo cat /var/log/syslog | grep -n 'Booting processor' 
``` Note the line number at the front of the last output line (say it is XXXX). Then do a ```
sudo cat /var/log/syslog | tail --lines=+XXXX > afile
``` to store the last boot messages to file "afile". Use an appropriate path instead of "afile".

[/INDENT]PS: You may want to _manually inspect and cleanup the syslog output before posting it here_, to verify that it does not disclose any information that you regard sensitive.

---

### Post by pharcycle on 2010-08-01
hi gzarkadas many thanks for the reply.

Since posting i was able to get my machine to boot mythbuntu by removing the affected hdd's and booting without them. Now with them attached again i can skip again when i boot, run gparted and 'check' them to again be able to mount the partition. Its really not too happy at the moment! 

My hdd setup is as follows:

1x 160gb sata for root and home (sda) ext 4 partition (unaffected)

1x 120gb sata with old data from previous installs (sdb) ext 4 partition (unaffected) mounted as /media/Secondary

2x 400gb sata for mytv recordings (sdc & sde) jfs partition (broken on boot) should be mounted as /media/Myth0 and media/Myth1

1x 1500gb sata for archive (sdd) and it previously had a system on so has partitions:

a. 400gb ext 4 for an old home (/media/old_home) (i think working at boot, will verify after writing this)
b. 50gb old root (ext 4, not mounted)
c. 1000gb jfs archive partition (/media/Archive) (broken at boot)

I followed your instructions and outputted my syslog from the last boot instance. I'm not sure exactly if this has everything you need but put in all the stuff about the hdd's i could see. I could e-mail you the full copy if need be (its 100kb)

I'd also set my fstab to mount the other partitions so all the entries after the swap partition are mine and had been working fine

I don't know if this is another symptom but my friends usb external hdd formatted as ntfs that wasn't connected at the time now doesn't automount properly when plugged in; it tries to mount it as the / filesystem by default and obviously fails.

My usual solution to most linux problems is to reformat and start over but as the live cd has the same problem i don't think it will go away this tim

"then try to run the appropriate tools (in this case jfs_fsck)  to correct them" not entirely sure how to do this, i ran 
```
jfs_fsck /dev/sdd7 -a 
``` but it failed saying bad superblock and some other text, not sure as i wasn't in a gui at the time and didn't think to save the text.

Thanks for taking a look.
David

EDIT: PS. should have mentioned that the gparted output was only for 2 of the drives, i thought since the fault was the same the info would probably be repeated

---

### Post by gzarkadas on 2010-08-02
First run from inside a terminal window the following set of commands (use the appropriate values for text within brackets) for each failing drive.

```

sudo jfs_fsck -n /dev/[your-failing-disk] > /home/[your-account]/[your-failing-disk]-jfs-log
sudo chown [your-account]:[your-account] /home/[your-account]/[your-failing-disk]-jfs-log

```These will report the errors and store them to the files sdd7-jfs-log, etc, inside your home folder. That way we will be able to see what are the errors.

---

### Post by pharcycle on 2010-08-02
Well, i'm really confused now,

I booted up my machine when i got home from work and it loaded up fine with no errors and i could get back into my partitions without having to check them. I unmounted one of the dodgy partitions and ran jfs_fsck and it reported back fine, vis:

```

jfs_fsck version 1.1.12, 24-Aug-2007
processing started: 8/2/2010 17.47.43
The current device is:  /dev/sdd7
Block size in bytes:  4096
Filesystem size in blocks:  254920960
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
**Phase 7 - Verify File/Directory Allocation Maps
**Phase 8 - Verify Disk Allocation Maps
1019683840 kilobytes total disk space.
     7155 kilobytes in 3175 directories.
470196432 kilobytes in 13424 user files.
        0 kilobytes in extended attributes
   207591 kilobytes reserved for system use.
549286972 kilobytes are available for use.
File system checked READ ONLY.
Filesystem is clean.
```

Since everything went wrong, mythtv won't let me watch live tv. I had this before after i set up the recording directories to the other 2 partitions and i had to chmod and chown the directories and it worked fine. I've done this again but it had no affect this time! 

All the mythtv logs I can find just tell me that live tv failed which i already knew! Given the problems are likely related, any further suggestions or something i could do to try and shed some more light on the problem?

Thanks.
Dave

---

### Post by pharcycle on 2010-08-02
It turned out to be the same problem as before with mythv, i erroneously changed the ownership to my username rather than mythtv... when i set it correctly it worked! 

i just wish i hadn't deleted all my channels now!

Thanks for the heads up with the partition problems, no doubt something else will go wrong soon (it always does!).

Dave

---

### Post by gzarkadas on 2010-08-02
Most probably, either the `jfs_fsck -a' you issued or the normal by init scripts attempt during boot up to fsck problematic filesystems or the combination of both in sequence has managed to recover the partitions.

JFS is designed to recover from such incidents; but it may in order to do so to sacrifice in some cases data that are unrepairable (this is common in such utilities, I suppose). So, it may be the case that you have lost some changes or even files or directories related to MythTV and thus it is now broken. 

I can't help with MythTV; I have never installed it / tried to configure it. But there are some steps to see if (and what) losses in the affected filesystems occurred:

[LIST]
[*]Check the lost+found directories in each of the affected partitions; do they contain items?
[*]Review your MythTV configuration; are all config files ok?
[*]Review your MythTV installation; are all binaries there?
[/LIST]
If after that you still can't identify what's wrong, another possibility is to try and reinstall the MythTV packages.

==============================

PS: I am happy to see that the non-functioning of MythTV was easier than seemed initially :); this allows us to rest at last! (but have a look in lost+found anyway).

---

### Post by pharcycle on 2010-08-02
i only have a lost+found in my '/' filesystem and it doesn't have anythning. Is this normal behavior, it wouldn't let me in without sudo -s first?
```
david@htpc:/$ cd lost+found
bash: cd: lost+found: Permission denied
david@htpc:/$ sudo cd lost+found
[sudo] password for david: 
sudo: cd: command not found
david@htpc:/$ sudo -s
root@htpc:/# cd lost+found
root@htpc:/lost+found# ls
root@htpc:/lost+found# 

```Randomly while working through this, ubuntu decided to forget my keyboard layout! Ahh, the fun!

Thanks for your help.
David

---

### Post by gzarkadas on 2010-08-02
lost+found is for root's eyes only. There is one for each partition, not only for / (at least for the ext family of filesystems, which I have installed and can verify). I also found a reference to it in a jfs paper (page [http://jfs.sourceforge.net/](http://jfs.sourceforge.net/), link "Documentation"; then when the submenu opens, link "JFS Overview paper"), so I expected to be there also (at /media/Myth0 , /media/Myth1 and /media/Archive). But it may not be the case. 

Anyway, I wish no more trouble for the next months; once in a while our systems should be just working, nothing more :)!

---

