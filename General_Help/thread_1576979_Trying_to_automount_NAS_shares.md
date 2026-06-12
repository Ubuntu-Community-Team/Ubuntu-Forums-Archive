---
title: "Trying to automount NAS shares"
date: 2010-09-18
forum: General Help
---

### Post by phoenix40uk on 2010-09-18
Hi:
I have added the following 2 lines to /etc/fstab
//192.168.2.105/Backup  /media/backup  cifs  nounix,guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//192.168.2.105/Files  /media/files  cifs  nounix,guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

When I reboot, only the files share automounts. This is the same if I add another line then only that line automounts. It is always only the last line.   when I run sudo mount -a  the other shares mount. Can anyone offer any advice? running Ubuntu Lucid on a dell studio 15

---

### Post by lmarmisa on 2010-09-18
I recommend a workaround. Do not use the /etc/fstab for mounting the NAS folders. Use instead the /etc/rc.local file. 

Add your mount commands to this file (edit the file with root privileges):

```


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -t cifs -o options_here //192.168.2.105/Backup /media/backup  
mount -t cifs -o options_here //192.168.2.105/Files /media/files

exit 0


```

---

### Post by phoenix40uk on 2010-09-19
Hi:
Thanks for the reply. 
I have added 
mount -t cifs -o nounix //192.168.2.105/Backup /media/backup

to the /etc/rc.local file but still won't automount. When I type sudo mount -t cifs -o nounix //192.168.2.105/Backup /media/backup - the share mount with no problems.

Am I doing something wrong?

---

### Post by phoenix40uk on 2010-09-23
This is all getting a bit peculiar now.

I have 3 shares on my NAS:   files, backup and music

I only need music to be automatically mapped for songbird library.
I am happy just to browse network to the other shares. 
So - when fstab contains no entries I can browse all folders with no issues.
If I add an entry to mount music folder in fstab, the folder will mount, but when I try to browse the other shares on the NAS I am prompted for username/password. But none of these folders are password protected. Does not accept my login details that I use for pc

tried removing from fstab and adding to rc.local to mount share. Share does not mount. Tried adding sleep command to allow netqwork time to come up - still no joy. Can anyone offer any advice?

---

### Post by luvshines on 2010-09-23
What entry are you using for the ftab to mount CIFS shares ?

---

### Post by phoenix40uk on 2010-09-23
Hi: FSTAB info below - note I have added an entry in hosts file for cygnus

//cygnus/Backup    /media/backup        cifs    guest,rw,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
//cygnus/Music/ScottsMusic   /media/itunes          cifs    guest,rw,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
//cygnus/files    /media/files        cifs    guest,rw,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

Thanks

---

### Post by luvshines on 2010-09-23
Is that a typo or you actually using space in uid=1 000 ??

Easiest way to get to know what entries to use is , do a manual mount (the way u did with sudo mount ...)

Then cat /etc/mtab to check what entry system has created and use that
Source-[http://www.linuxquestions.org/questions/linux-newbie-8/cifs-mount-and-fstab-entries-725777/](http://www.linuxquestions.org/questions/linux-newbie-8/cifs-mount-and-fstab-entries-725777/)) :)

See if it helps.

---

### Post by phoenix40uk on 2010-09-23
Hi:
 It's a typo mate. There's no space.
okay did a manual mount then a cat /etc/mtab.
results below

scott@Defiant ~ $ sudo mount -t cifs -o nounix //192.168.2.105/Backup /media/backup
Password: 
scott@Defiant ~ $ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
//192.168.2.105/Backup /media/backup cifs rw,mand 0 0

---

### Post by luvshines on 2010-09-23
Did you try using the last entry that is shown in /etc/mtab :

//192.168.2.105/Backup /media/backup cifs rw,mand 0 0

in /etc/fstab ??

---

### Post by phoenix40uk on 2010-09-25
Hi:

No luck I'm afraid - shares did not automount.

However - I went back to fstab method - and it seems that If I start laptop but do not log in for 60-90 seconds, all 3 shares will automount. this does tie in because when I run sudo mount -a it does take a short time to mount the shares

---

### Post by phoenix40uk on 2010-09-27
okay - sorted this now. Just moved all folders on NAS into 1. So only 1 drive to mount and it does so right away. Job done. THis can be marked as solved.

---

