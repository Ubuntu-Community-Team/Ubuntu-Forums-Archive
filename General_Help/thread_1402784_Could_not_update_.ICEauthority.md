---
title: "Could not update .ICEauthority"
date: 2010-02-09
forum: General Help
---

### Post by xcrunner78 on 2010-02-09
Okay, I'm a newbie to Ubuntu (Using Karmic Koala 9.10).  When I installed the new OS I partitioned the hard-drive with G-Parted Live 0.5.0-1 so that I would have equal partitions.  I wanted to store all my data on the second partition and the OS on the first.  After everything was installed I used instructions on [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to move my home directory to the new partition.  In the terminal I typed:

sudo mkdir /old
sudo mount -t ext4 */dev/sda1* /old
sudo mkdir /new
sudo mount -t ext4 */dev/sda3* /new
cd /old/home
f*sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/*
sudo mv /old/home /old/home_backup
sudo mkdir /old/home
sudo cp /old/etc/fstab /old/etc/fstab_backup
gksudo gedit /old/etc/fstab

in Gedit I typed: */dev/sda3* /home ext4 nodev,nosuid 0 2

The after I did that I saw that everything was moved.  I tested it by typing something in openoffice.org and save it, but it saved it to the old home in the first partition.  So I thought that I did something wrong so I try redoing all of my steps in the terminal.  After retyping the command I rebooted  and afetr I logged in the error came up:

"Could not update .ICEauthority file home/jason/,ICEauthority"

then I clicked okay and another error of:

"There is a problem with the configuration server (/usr/lib/libcof2-4/conf-sanity-check-2 exited with status 256)"

I started up with Karmic Koala live disk and moved my files from /home_backup/ to /home/.  I looked for the hidden file of .ICEauthority and could not find it anywhere.

After rebooting and logging in, I came up with the same errors.  I am lost and have no idea what to do.  Any suggestions?

---

### Post by frogotronic on 2010-02-13
**bump**

---

### Post by darolu on 2010-02-13
It seems to be a permissions problem to me; first make sure you are the owner of the .ICEauthority file; try to do it logging in as root this files permissions are 600 and if the owner is root you won't be able to see it with your regular username, if that doesn't work then make sure you want those options for your home.

> 
nodev = Do not interpret character or block special devices on the file system.

nosuid = Do not allow set-user-identifier or set-group-identifier bits to take effect. (This seems safe, but is in fact rather unsafe if you have suidperl(1) installed.)

from: [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

I've seen than /home usually have relatime option only.

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

