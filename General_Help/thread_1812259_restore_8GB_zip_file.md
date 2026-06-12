---
title: "restore 8GB zip file"
date: 2011-07-26
forum: General Help
---

### Post by DrScum on 2011-07-26
I created a zip file from a folder which ended up being about 8GB. Burned the zip on a double layer DVD. Now I want to restore from the DVD but it's not visible in the file manager. Any ideas out there?

---

### Post by DawieS on 2011-07-26
The default 10.04 installation is not able to read DVD's, probably to avoid possible legal issues in some countries.
To be able to read DVD's, you have to install an additional repository and library. Open a terminal and type:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get -q update
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
sudo apt-get -q update
sudo aptitude install libdvdcss2
```

---

### Post by DrScum on 2011-07-26
Thanks for the reply DawieS. I did what you suggested. When I insert the DVD in the drive it doesn't mount and when I try to mount it manually I get the following:

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by DawieS on 2011-07-26
Are you able to read other dvd's ?
Was the dvd burned from the same dvd writer?

If you want to automount when inserting cd's or dvd's , enable **Browse media when inserted** at Nautilus > Edit > Preferences > Media.

Edit:
You can also install **Brasero** in Synaptic Package Manager. From **Brasero**, copy an image of the dvd onto your hard disk. If you get errors, try lower reading speeds.

---

### Post by DrScum on 2011-07-26
Other CDs and most DVDs automount, the box in Nautilus is checked. 

But I do have the problem with some DVDs that they mount with restricted access. The message when trying to access with file manager is:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "VIDEO_TS"

This is in fact very annoying

---

