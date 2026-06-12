---
title: "Password Messup"
date: 2010-03-30
forum: General Help
---

### Post by Zyik on 2010-03-30
Hello, I'm a first time user of Ubuntu. I've been hearing good things about Ubuntu and other Linux systems for years. Yesterday I decided that I would dual boot my laptop, a vista home, machine, with Ubuntu to try it out and have a terminal that I needed for my computer science class projects. It went through perfectly, however when I try to enter the password I entered at the beginning it says it's not the right one. I've tried all variations of it, and typos of it, and it doesn't work. Is there anyway to wipe it and reinstall Ubuntu without getting ride of my vista? I have a lot of games and the like saved on there that I would like to keep.   

       -Lucy

---

### Post by cjhabs on 2010-03-30
> **Zyik said:**
> Hello, I'm a first time user of Ubuntu. I've been hearing good things about Ubuntu and other Linux systems for years. Yesterday I decided that I would dual boot my laptop, a vista home, machine, with Ubuntu to try it out and have a terminal that I needed for my computer science class projects. It went through perfectly, however when I try to enter the password I entered at the beginning it says it's not the right one. I've tried all variations of it, and typos of it, and it doesn't work. Is there anyway to wipe it and reinstall Ubuntu without getting ride of my vista? I have a lot of games and the like saved on there that I would like to keep.   

       -Lucy

You should be able to do the following to fix this:
Boot off the Ubuntu live cd
Mount your root filesystem, for example under /mnt
For example, if it is /dev/sda1 then:
    mount /dev/sda1 /mnt
Then:
    chroot /mnt
    passwd username
(where username is the username you can;t currently log in as)
Enter a new password when it asks.
    pwconv

Reboot into the disk based Ubuntu and try logging in again.

---

### Post by sisco311 on 2010-03-30
No need for a LiveCD, you can reset the password from the recovery mode:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by cjhabs on 2010-03-30
> **sisco311 said:**
> No need for a LiveCD, you can reset the password from the recovery mode:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

I never knew that - I've never even seen my grub menu - thanks for the info!

---

### Post by sisco311 on 2010-03-30
> **cjhabs said:**
> I never knew that - I've never even seen my grub menu - thanks for the info!

You're welcome!

Yep, by default, in Karmic, on a single boot system the grub menu is hidden. To get the menu you have to hold down the SHIFT key during the bootup.

On a *traditional* Linux distro you have to enter the root password to access the single user mode (a.k.a recovery mode), but since the root account password is locked by default, sulogin is patched to handle the default case of a locked root password.

I really like your solution, that will work even if one enables the root account password. Of course there is an easier way to boot in a root shell without being prompted for a root password even if the root password is enabled. :) At the boot menu you can press e to edit the grub menu entry & boot with the *init=/bin/bash* kernel parameters.

But of course, chroot is cool & efficient tool for diagnosing and repairing a broken system. You may be interested so here is the script I use to chroot in my lucid installation:
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

---

### Post by Zyik on 2010-03-30
Thank you guys so much! I'm so glad I don't have to get rid of my games. =)

---

