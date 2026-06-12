---
title: "Ubuntu 9.10 lost root password"
date: 2010-04-01
forum: General Help
---

### Post by rotatingastrothing on 2010-04-01
Hi, I've managed to lose my root password. I've seen a load of suggestions of what to do and none of them work. 

I've tried pressing "e" at the grub startup and replacing "ro" with "rw init=/bin/bash" or "rw init=/bin/bw" the first causes the machine to hang, the second does nothing.

I've tried booting into recovery mode and opening a root shell. This requires the root password which I don't have.

I've tried booting from my installation stick, it went into the installation menu, none of the options looked useful.

Any ideas on how to recover/reset the root password? I'm running 9.10 with Grub 1.97

And yes I know I shouldn't have set a root password.

---

### Post by Nisal on 2010-04-01
try this

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by damis648 on 2010-04-01
You may be able to chroot into the installation to change the password. See [this]("http://ubuntuforums.org/showpost.php?p=9058675&postcount=3") post, and at the part where it says "run whatever commands you need", just run
```
passwd root
```
and it should work AFAIK.

---

### Post by sisco311 on 2010-04-01
If you have an account with sudo rights, you can use it to disable or reset the root account password:
```
sudo passwd root
```
or
```
sudo usermod -p ! root
```
_Don't_ disable the root password if you _don't_ have an account with full sudo privileges!

--------------------------------------------------------------------------

In the grub menu entry you have to replace "ro quiet splash" with "rw init=/bin/sh" (or "rw init=/bin/bash").

--------------------------------------------------------------------------

damis648 is right, you can boot a Live CD or Live USB, chroot into Ubuntu and disable or reset the root password. 

Try this script to chroot into Ubuntu:
```
#!/bin/bash

############################################################################
# variables                                                                #
############################################################################

# device name of the root partition
ROOT="**/dev/sda1**"

# mount point of the new root partition
MOUNT="/mnt/ubuntu"

# list of virtual filesystems and additional config files
ARGS="dev dev/pts proc sys etc/resolv.conf"

# list of additional devices and their mount pont. 
# device names must be separated by the mount point with a colon:
# i.e. /dev/sda2:/home 
AMOUNT=""

# user name
UNAME="root"

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
Replace /dev/sda1 with the device name of your root partition. Type:
```
sudo blkid
```
or
```
sudo fdisk -l
```to list the partitions.

Run the script as root:
```
sudo path/to/script
```

--------------------------------------------------------------------------

If nothing else works, mount the root partition & manually edit the /etc/shadow file.

The fields in the file are separated by a colon [noparse](:)[/noparse], the second field is the password:
```
root:[COLOR="Red"]$6$3wIc6.X6$fAxvPrOxA3258d5nlkysaVusWFbakjgwC9j5eXyp9hJ9BcWlGmP.638GHTZGS6tqLu5uR4c.a/MBjfaIpEEZK.[/COLOR]:14700::::::
```
replace the hash with 00xQPHYlVDIw6:
```
root:[COLOR="Red"]00xQPHYlVDIw6[/COLOR]:14700::::::
```
this changes the root password to **password**. Once you are able to su to root change the root password to a strong one.

---

### Post by rotatingastrothing on 2010-04-02
OK, sisco 331's solution 


--------------------------------------------------------------------------

In the grub menu entry you have to replace "ro quiet splash" with "rw  init=/bin/sh" (or "rw init=/bin/bash").

--------------------------------------------------------------------------

got me into a root shel but I still have password problems. Have reinstalled and currently reloading data. I was going to reinstall in a month or so anyway.

Niall

---

