---
title: "Ubuntu 8.04 won't boot (&quot;fsck died&quot;)"
date: 2011-02-20
forum: General Help
---

### Post by ronbuntu on 2011-02-20
Hi, I am running Ubuntu 8.04 (RAID mirror, 5 hard drives).  System won't boot.

> fsck 1.40.8 (13-March-2008)
/dev/md0: clean, 309499/15269888 files, 1952585/61048976 blocks
                                                                                                                                       [OK]
Checking file systems...
1246
fsck 1.40.8 (13-March-2008)
 fsck.ext3: Unable to resolve 'UUID=d6e3b042-f41a-46cc-8b36-4709944e8ecd'
fsck died with exit status 8
                                                                                                                   [fail]
                      * File system check failed.
A log is being saved in  /var/log/fsck/checkfs if that location is writable.
 Please repair the system manually.
  A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
                     bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@ubuntu:~#
Entering "Reboot" led to this dialog box ...

> /etc./gdm/Xsession: Beginning session setup...
Can't create dir /home/ron/Desktop
Can't create dir /home/ron/Desktop
Can't create dir /home/ron/Templates
Can't create dir /home/ron/Public
Can't create dir /home/ron/Documents
Can't create dir /home/ron/Music
                       Can't create dir /home/ron/Pictures
Can't create dir /home/ron/Video
Setting IM through im-switch for locale=en_US.
Start IM through /etc./X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
                       
(seahorse-agent:6975): libgnomevfs-WARNING **: Unable to create ~/gnome2 directory: No such file or directory
(seahorse-agent:6975): libgnomevfs-WARNING **: Unable to create ~/gnome2 directory: Permission denied.
                       Could not create per-user gnome configuration directory '/home/ron/.gnome2/': No such file or directory
System asked for failsafe session, but I don't have one.  I ended up back at the aforementioned root@ubunt prompt.  One friend (we'll call him G-Man) thought the main hard drive might be dead.  He asked if there were any strange noises coming from the tower.  I said no.  Then he recommended downloading an Ubuntu Live CD and doing a repair install.  That led to the following error:

"Rescuing a Broken System:
There is no dedicated rescue mode on this CD."

A second friend (we'll call him D-Day) suggested running GParted from the Ubuntu 9.04 Live CD (sorry about all the dots, but I was having trouble getting this to display properly).

> Partition...........File System.......Size..................Used..........Unused............Flags
/dev/sda1........ext3..................232.88 GB........7.45 GB......225.43 GB.........boot, raid
/dev/sdb1........ext3..................232.88 GB........7.45 GB......225.43 GB.........boot, raid
/dev/sdc1........unknown............456.76 GB............ --................--..................raid
/dev/sdd1........unknown............456.76 GB..............--...............--..................raid
      /dev/sde1........unknown............456.76 GB.............--................--..................raidD-Day said:
"If you can see the partitions, mount any that aren't mounted.  A quick guide can be found: <[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)>.  Pay close attention to the step indicated by **ls -l /dev/disk/by-uuid** and see if the unknown UUID (d6e3b042-f41a-46cc-8b36-4709944e8ecd) appears in the list.  Once all drives are mounted, verify you can access data on all of them, then just manually run **fsck** on each drive.  If mounting via this guide doesn't work, you'll need to try mounting manually, but try this first."

Unfortunately, this didn't go so well.  Here are some commands that I ran, and the results ...

> sudo mkdir /storage
ls -l /dev/disk
total 0
drwxr-xr-x 2 root root 440 2011-27 04:17 by-id
drwxr-xr-x 2 root root   60 2011-27 04:17 by-label
drwxr-xr-x 2 root root 260 2011-27 04:16 by-path
ls -l /dev/disk/by-uuid

 ls: cannot access dev/disk/by-uuid: No such file or directory
ls -l /dev/sda1
brw-rw---- 1 root disk 8, 1 2011-01-27 04:16 /dev/sda1
ls -l /dev/sda1/by-uuid
ls: cannot access dev/sda1/by-uuid: No such file or directoryThe good new is that I have backed up most (but not all) of my data.  The bad news is that I didn't clone the system for restore purposes.  Can anyone help?

---

