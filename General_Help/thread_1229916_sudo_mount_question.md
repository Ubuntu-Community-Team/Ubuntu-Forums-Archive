---
title: "sudo mount question"
date: 2009-08-02
forum: General Help
---

### Post by gurpal2000 on 2009-08-02
Hi
I'm new to sudoers and have read the doco, but i can't seem to figure this out.
I am able to mount/unmount partitions from the rest of the system! I would like user "homeuser" to be ONLY able to run mount/umount with the following patterns strictly.
Is it because "homeuser" is able to "Administer the system" under Users and Groups?

Does the wilcard pattern look correct below? I think %u means current user?

Thanks

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
homeuser ALL=NOPASSWD: /bin/mount -t cifs //*/* /home/%u/*
homeuser ALL=NOPASSWD: /bin/umount /home/%u/*

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by gurpal2000 on 2009-08-19
bump - any ideas?

---

### Post by MaxIBoy on 2009-08-19
Your best bet, instead of doing voodoo magic with wildcards in your sudoers file, is to create shell scripts to do your mounting. This will make it easier to restrict what type of mounting is allowed.

In a simplistic example, you create one of these for every user on the system who you want to give these privileges to.
```
#! /bin/bash
# a simple script to unmount a directory in the homedir of a user calling it.
# this file is /bin/umountDirHomeuser.sh
# to create a version for a different user replace "Homeuser" with the desired username.
# to run this script, simply type "sudo umountDirHomeuser [NAME OF MOUNTPOINT]
# for example "sudo umountDirHomeuser Music" (if Music is on its own partition.)
# "sudo umountDirHomeuser ~/Music" will NOT WORK! 
# "sudo umountDirHomeuser /home/homeuser/Music" will NOT WORK!




#adjust the following line of code depending on the name of the user you are targeting.
TARGET_USER_HOMEDIR="/home/homeuser"
DIR_TO_UNMOUNT=$TARGET_USER_HOMEDIR$1
umount DIR_TO_UNMOUNT
 
```
Give the user permission to only execute that particular script with sudo, and it will work.


If you want I can write the script to mount things as well.

---

### Post by gurpal2000 on 2009-08-22
> **MaxIBoy said:**
> Your best bet, instead of doing voodoo magic with wildcards in your sudoers file, is to create shell scripts to do your mounting. This will make it easier to restrict what type of mounting is allowed.

In a simplistic example, you create one of these for every user on the system who you want to give these privileges to.
```
#! /bin/bash
# a simple script to unmount a directory in the homedir of a user calling it.
# this file is /bin/umountDirHomeuser.sh
# to create a version for a different user replace "Homeuser" with the desired username.
# to run this script, simply type "sudo umountDirHomeuser [NAME OF MOUNTPOINT]
# for example "sudo umountDirHomeuser Music" (if Music is on its own partition.)
# "sudo umountDirHomeuser ~/Music" will NOT WORK! 
# "sudo umountDirHomeuser /home/homeuser/Music" will NOT WORK!




#adjust the following line of code depending on the name of the user you are targeting.
TARGET_USER_HOMEDIR="/home/homeuser"
DIR_TO_UNMOUNT=$TARGET_USER_HOMEDIR$1
umount DIR_TO_UNMOUNT
 
```Give the user permission to only execute that particular script with sudo, and it will work.


If you want I can write the script to mount things as well.

ok that would work. Thanks i'll have a go at writing those.
thx

---

