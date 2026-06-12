---
title: "no space left on device!"
date: 2010-01-09
forum: General Help
---

### Post by bootdoc on 2010-01-09
just reinstalled because of this very issue.  20gb for the root partition 5gigs for /var.  WTF IS UP WITH THE SPACE DEAL!

---

### Post by ajgreeny on 2010-01-09
More explanation needed please.  Is that the sizes of your root and /var partitions?  If not, what else do you mean?

Normally a complete new install with nothing added and just the default files/folders in home would be about 2.5 - 3.0GB.  If you are using 20GB with a new install and no personal files in home, there is something most definitely wrong.

---

### Post by bootdoc on 2010-01-09
i made the / 20gb and /var 5gb to avoid the no space issue.  i am not at home at the moment so i can't run disk analyzer.  it is a very frustrating issue, an issue that should NOT be.

---

### Post by oldos2er on 2010-01-09
Perhaps when you get home, you can post the output from **sudo fdisk -l**

---

### Post by ajgreeny on 2010-01-09
And also the output from command ```
df -h
```

---

### Post by bootdoc on 2010-01-09
sudo fdisk -l
[sudo] password for charlie: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c5a60

  [COLOR="Green"] Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         124      995998+  83  Linux
/dev/sda2             125       30401   243200002+   5  Extended
/dev/sda5             125         746     4996183+  83  Linux
/dev/sda6             747        3236    20000893+  83  Linux
/dev/sda7            3237       30401   218202831   83  Linux[/COLOR]

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005f9da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    5  Extended
/dev/sdb5               1       13054   104856192   83  Linux
/dev/sdb6           13055       26108   104856223+  83  Linux
/dev/sdb7           26109       39162   104856223+  83  Linux
/dev/sdb8           39163       52216   104856223+  83  Linux
/dev/sdb9           52217       65270   104856223+  83  Linux
/dev/sdb10          65271       78324   104856223+  83  Linux
/dev/sdb11          78325      121601   347622471   83  Linux

/dev/sdb is a backup disk I just installed.  

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              19G  7.6G   11G  43% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  236K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  216K  994M   1% /dev
tmpfs                 994M  1.1M  993M   1% /dev/shm
lrm                   994M  2.5M  992M   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda1             958M   81M  828M   9% /boot
/dev/sda7             205G  201G     0 100% /home
/dev/sda5             4.7G  1.1G  3.4G  25% /var
/dev/sdb5              99G  188M   94G   1% /media/charlie
/dev/sdb6              99G  188M   94G   1% /media/prisca
/dev/sdb7              99G  188M   94G   1% /media/music
/dev/sdb8              99G  188M   94G   1% /media/videos
/dev/sdb9              99G  188M   94G   1% /media/audio
/dev/sdb10             99G  188M   94G   1% /media/video
/dev/sdb11            327G   57G  254G  19% /media/backup

/home shows 100% used! WTF!  it's 205 gigs!  This is what i don't understand.  

I open openoffice and get an error saying no more space in /home/charlie/.openoffice.org/3/user. the size of this folder is 1.7mb.  How is it that one little folder can f'up the whole deal.  I also had backup2l creating backups in /home/charlie/backup which has taken up some space and i have moved it to /media/backup.

Is there some kind of size minimum for folders that I have not heard of??  I have been using linux since RH6.2 and debian since Fedora (reason i switched to debian) came out and have never had this problem until recently.  I think it is ridiculous that one folder on a 205 gig partition can create this kind of problem.

I certainly have never had a problem with openoffice like this before.

---

### Post by john newbuntu on 2010-01-09
Go to /home and run the command:
du -k | sort -n
and look at the last 50 odd files/directories for a possible cleanup/investigation.

---

### Post by bootdoc on 2010-01-09
Ok, as it turns out my backup folder in /home/charlie was over 193gigs.  So I guess that was a problem.   I will report back after the move is done.

---

### Post by bootdoc on 2010-01-09
the move of /home/charlie/backup to /media/backup is finished and /home/charlie/openoffice.org/3/user is still at 98.9%.  Should I delete the .openoffice.org folder and log in again?

---

### Post by michy99 on 2010-01-09
After moving the backup folder, did you delete the original? When you do a mv to a different partiton, it leaves the original in place unless you delete it.

---

### Post by bootdoc on 2010-01-10
i deleted the original backup, also deleted .openoffice.org.  things seem to be better.  i am a little concerned that the openoffice folder filled up after using open office twice since reinstalling.

---

### Post by michy99 on 2010-01-10
A folder has as much free space as the partition on which it resides. It could be anything on that partition that is taking up space. When you say you deleted the original backup, how did you do it? Are you sure it isn't still in Trash?

---

### Post by drs305 on 2010-01-10
These guides might provide some insight about disk space. Did you empty your trash bin after deleting the files. Until you do so, the deleted items still take up space. 

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

[How To: Disk Full? Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

The topics don't cover your situation specifically but you may find reference to something you are doing that is causing the partition to fill up.

---

