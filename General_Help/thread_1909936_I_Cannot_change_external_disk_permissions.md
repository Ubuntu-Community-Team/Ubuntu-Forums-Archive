---
title: "I Cannot change external disk permissions?"
date: 2012-01-16
forum: General Help
---

### Post by cd-r80 on 2012-01-16
Im running USB live (stick) and trying to use extenal Usb Disk EXT3. I cannot set permissions 775 or 777 for files on external why? Nothing just happens. sudo chmod 777 /media/disk/* etc.

---

### Post by Wayne_V on 2012-01-16
is it mounted read only?  (see the output of "mount")

try "tail -f /var/log/{dmesg,*log}" in another terminal when you try to chmod and check for errors.

---

### Post by WorMzy on 2012-01-16
Maybe it's mounted read only?

What does ```
mount
``` say about it?

---

### Post by cd-r80 on 2012-01-16
It says: /dev/sdb1 on /media/snip type ext3rw,nosuid,nodev,uhelper=udisks 

Read & Write?

Perhaps my command is not right? trying All folders files and subfolders:
chmod -R 775 /media/d........

---

### Post by WorMzy on 2012-01-16
Looks like it. Any error messages in ```
dmesg
``` about it?

EDIT: Oops, didn't see Wayne_V's post. Try his command for examining log files and see if that yields anything.

---

### Post by cd-r80 on 2012-01-16
nothing special appears. Only auth.log:
ubuntu : TTY=pts/1 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/bin/chmod -R 775 /media/d1655

---

### Post by t0p on 2012-01-16
Could it be a permissions problem?  You could try the following: press **Alt+F2**, then in the "Run Application" box that appears, type in 

```
gksudo nautilus
```

This will open a file manager window with administrative permissions.  Now you should be able to navigate to the external drive and, under **Properties**, change ownership to your regular user account.

Just be careful, and close the administrative file manager window when you're done.

---

### Post by WorMzy on 2012-01-16
That's just a record of you running that command with sudo.

Are you sure that the permissions haven't changed?

```
ls -l /media/d1655 
```

---

### Post by cd-r80 on 2012-01-16
Nautilus is annoying when trying to change permissions. I cannot go down on user list to live user it just jumps up and down.Also  I cannot do this for many files... too slow.

---

### Post by cd-r80 on 2012-01-16
Oh I see the rights have changed but Nautilus still has them locked...? 


Ok  I used chown -R ubuntu /med... for now
I have been confused with user 1000 & ubuntu live user... Live has id 1000 and....

---

