---
title: "Boot dead ubuntu installation from live cd?"
date: 2010-03-27
forum: General Help
---

### Post by daswerth on 2010-03-27
I just installed Windows 7, so my grub is gone.  I was wondering if there is a way to use a live cd to boot into my ubuntu partition.  I'm likely going to scrap my ubuntu partition soon, so I don't want to mess with installing grub.  I just need to run ubuntu once to recover some application data.

Thanks :)

---

### Post by jerrrys on 2010-03-28
run your live cd and in your home folder on the live cd (if it can see it) you should see this

[ATTACH]151705[/ATTACH]

that will be your hdd install

---

### Post by daswerth on 2010-03-28
Sorry, I know how to access the partitions by running the live cd.  Re-reading my original post, I can tell I didn't clearly explain what I'm trying to do.

What I would like to do is boot into my old installation so that I can run VirtualBox and retrieve some data from a virtual machine.  I'm thinking it would be easier to boot into this old installation than it would be to copy the virtual machines into Windows and try to reconfigure them.

---

### Post by jerrrys on 2010-03-28
i do not use virtualbox, so sorry but can't help..a thought...somehow add virtualbox to your thread title and see if that helps you get a hit...

---

### Post by oldfred on 2010-03-28
Is is not that difficult to install grub, get your data and reinstall windows boot loader. It takes longer to pop in CD and load it than to install a new MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by sisco311 on 2010-03-28
You can [chroot]("http://en.wikipedia.org/wiki/Chroot") into the Ubuntu installaton. Here is the script I use:
```

#!/bin/bash

############################################################################
# variables                                                                #
############################################################################

# device name of the root partition
ROOT="/dev/sda1"

# mount point of the new root partition
MOUNT="/mnt/lucid"

# list of virtual filesystems and additional config files
ARGS="dev dev/pts proc sys etc/resolv.conf"

# list of additional devices and their mount pont. 
# device names must be separated by the mount point with a colon:
# i.e. /dev/sda2:/home 
AMOUNT=""

# user name
UNAME="sisco"

############################################################################
# start the chroot environment                                             #
############################################################################

# add user to the list of allowed users to make connections to the X server.
sudo -u $USER xhost SI:localuser:$UNAME

# create the mount point & mount the root partition
mkdir -p $MOUNT
mount $ROOT $MOUNT

# mount the virtual filesystems & resolv.conf to enable the network
for i in $ARGS; do
  mount --bind /$i $MOUNT/$i
done 

# mount additional partitions:
for i in $AMOUNT; do
  mkdir -p ${MOUNT}${i//*:/}
  mount ${i//:*/} ${MOUNT}${i//*:/}
done

# chroot into the linux installation
chroot $MOUNT su - $UNAME 

```

Edit the **variables** section, save the file and run it as root (sudo ./scriptname). 

In the chroot environment you can run virtualbox or any other application.

---

