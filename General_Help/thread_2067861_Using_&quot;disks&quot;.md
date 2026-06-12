---
title: "Using &quot;disks&quot;"
date: 2012-10-07
forum: General Help
---

### Post by stephenran on 2012-10-07
I want to edit the mount options for my harddrives (namely, have them automount on startup).  Now I know you can do this via the terminal using fstab etc, but I don't feel like I should have to. The options for editing mount options in "drives" are always greyed out, and I assume that if I ran the utility with elevated privileges I would be able to access them. 

The issue is that I don't know the name of the actual service "disks" so I can't just run something like "sudo disks".  I can't right click and hit something like "run with elevated privileges" either (but I really wish I could).

I assume there it a fairly simple solution to this, but I feel  like it should be much more intuitive to find the solution. Disks is ALMOST a super simple and useful utility, and I just want to find out how to make it that way. 

Thanks in advance for any help here.

---

### Post by sienile on 2012-10-07
I've never used "disks"; but for setting mount points via GUI, I use MountManager (available in Software Center).

It does the job great with only one small glitch. If you mount to a directory with a space in the name, it writes to fstab exactly as shown... not with the \040 code for spaces. To fix it, just open fstab as root and manually replace the space with \040.

---

### Post by bab1 on 2012-10-08
> **stephenran said:**
> I want to edit the mount options for my harddrives (namely, have them automount on startup).  Now I know you can do this via the terminal using fstab etc, but I don't feel like I should have to. The options for editing mount options in "drives" are always greyed out, and I assume that if I ran the utility with elevated privileges I would be able to access them. 

The issue is that I don't know the name of the actual service "disks" so I can't just run something like "sudo disks".  I can't right click and hit something like "run with elevated privileges" either (but I really wish I could).

I assume there it a fairly simple solution to this, but I feel  like it should be much more intuitive to find the solution. Disks is ALMOST a super simple and useful utility, and I just want to find out how to make it that way. 

Thanks in advance for any help here.

To run the disks utility as the root user from the CLI use this```
sudo palimpsest
```

---

### Post by stephenran on 2012-10-11
> **bab1 said:**
> To run the disks utility as the root user from the CLI use this```
sudo palimpsest
```

> 
butters@buttershaus:~$ sudo palimpsest
[sudo] password for butters: 
sudo: palimpsest: command not found
butters@buttershaus:~$ sudo apt-get install palimpsest
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package palimpsest
butters@buttershaus:~$ 


mount manager even when run as root is still giving me greyed out mount options. I'm thinking it has to do with the permissions problem with NTFS disks.  If I format the disks in ext4 do you think the issue would be resolved?  

When I change the permissions of the drives they always get reverted, and I've installed the ntfs utilities already. since I don't plan on going back to windows any time soon I'm thinking I might just switch over to ext4.  If I do, will the windows computers in the network have trouble viewing files on the drives?

---

### Post by oldos2er on 2012-10-11
Palimpsest is the package **gnome-disk-utility**

NTFS partitions don't understand Linux permissions. More info:

[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab](http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab)

---

### Post by bab1 on 2012-10-11
> **stephenran said:**
> ...I might just switch over to ext4.  If I do, will the windows computers in the network have trouble viewing files on the drives?

Both Windows and Linux have drivers for NTFS and EXT file systems.  Linux probably does a better job with NTFS than Windows does with EXT.  Both can use SMB/CIFS if you share the folder in question.

The larger question is how are the HDD's connected to the local host?  Is it USB or SATA.  Do the HDD's get moved to another machine (OS) from time to time?

---

### Post by stephenran on 2012-10-11
The disks are all connected through sata. They are internal HDDs inside my machine that will not be moved.

---

### Post by bab1 on 2012-10-11
> **stephenran said:**
> The disks are all connected through sata. They are internal HDDs inside my machine that will not be moved.


Are you dual booting this machine?  Why are the partitions on the disks formatted to NTFS in the first place?  How do the *"...the windows computers in the network * access the data on the partitions now?

---

### Post by stephenran on 2012-10-11
I'm not dual booting, they were formatted to NTFS because I was using windows until just a few weeks ago. I set up a samba share so that the windows computers (and the mac) can access them.  They just go to network locations and access all the files on the drive from windows explorer, or from finder on the mac.

---

### Post by bab1 on 2012-10-11
> **stephenran said:**
> I'm not dual booting, they were formatted to NTFS because I was using windows until just a few weeks ago. I set up a samba share so that the windows computers (and the mac) can access them.  They just go to network locations and access all the files on the drive from windows explorer, or from finder on the mac.

They will be more manageable if they are formatted ext4 and mounted via fstab.  The OS that is local to the machine (in this case Ubuntu) should be the determining factor.  The remote hosts ( windows computers and the mac) will still work the same as now since you are using Samba (CIFS) to share files and directories.

The setup of the shares in smb.conf will change as the paths to the files will change.  Everything else is the same.  You should be able to manage remote users better with these re-formatted drives.

---

### Post by stephenran on 2012-10-14
> **bab1 said:**
> They will be more manageable if they are formatted ext4 and mounted via fstab.  The OS that is local to the machine (in this case Ubuntu) should be the determining factor.  The remote hosts ( windows computers and the mac) will still work the same as now since you are using Samba (CIFS) to share files and directories.

The setup of the shares in smb.conf will change as the paths to the files will change.  Everything else is the same.  You should be able to manage remote users better with these re-formatted drives.


Thank you very much for the info! Also sorry for my slow reply, it's midterm season :-/

---

