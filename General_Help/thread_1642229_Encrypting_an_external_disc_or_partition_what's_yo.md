---
title: "Encrypting an external disc or partition: what's your way of doing it?"
date: 2010-12-10
forum: General Help
---

### Post by ruipedroca on 2010-12-10
Hi,

Encrypting an external disc or partition: what's your way of doing it? :guitar:

My way:
Several times I have to encrypt external discs.
I use GdeCrypt, LUKS and Ext3, but sometimes I have to stop it and start all over because it doesn't finish the job no matter how many days it runs (I believe that why it's still in the 0.7xx version).
Once it's done, I'm happy with it and never had a problem.

However, I'd prefer a way of doing it which aloud me to check the progress.
If you know how, please share it! ;)

---

### Post by Qwerty_ls on 2011-01-30
Hi,
 I've recently installed Gdecrypt but it doesn't work at all.
It doesn't create the partition even if I leave it running for hours.

I'm trying to create the volume in a USB stick of 1GB.

Any help? Thanks in advance.

---

### Post by septekin on 2011-01-30
I've used TrueCrypt to encrypt parts of three external hard disks so far with no problems. Google the term for further info. They are at [http://www.truecrypt.org](http://www.truecrypt.org).

Good luck.

---

### Post by Qwerty_ls on 2011-02-04
Thank you septekin for your reply.
I googled truecrypt but it seems that the truecrypt developers are not using a real open source license. I would like to use gdecrypt since it is in the native repositories of ubuntu.

---

### Post by vcrpcant on 2011-02-04
> **Qwerty_ls said:**
> Thank you ruipedroca for your reply.
I believe you ment to thank septekin.


Hope this helps:

SHORT VERSION
1  sudo apt-get install cryptsetup
2  sudo badblocks -c 10240 -s -w -t random -v /dev/sdx
3  sudo modprobe dm-crypt
4  sudo modprobe sha256
5  sudo modprobe aes
6  sudo cryptsetup --verify-passphrase luksFormat /dev/sdx1 -c aes -s 256 -h sha256 
7  sudo cryptsetup luksOpen /dev/sdx1 500usb3
8  sudo mkfs -t ext3 -m 1 -O dir_index,filetype,sparse_super /dev/mapper/500usb3
note: replace /dev/sdx or /dev/sdx1 with your specific disk or partition



LONG VERSION
1 sudo apt-get install cryptsetup
2 sudo badblocks -c 10240 -s -w -t random -v /dev/sdx

3 create a partition with gparted or fdisk

4 sudo modprobe dm-crypt
5 sudo modprobe sha256
6 sudo modprobe aes

Run the following command to encrypt the /dev/sdx1  partition:
7 sudo cryptsetup --verify-passphrase luksFormat /dev/sdx1 -c aes -s 256 -h sha256

The encrypted partition will now need to be unlocked and mapped to /dev/mapper/securebackup using the following command:
7 sudo cryptsetup luksOpen /dev/sdx1 securebackup

The encrypted partition is now available to be formatted with a filesystem - in this example, ext3 as follows:
8 sudo mkfs -t ext3 -m 1 -O dir_index,filetype,sparse_super /dev/mapper/securebackup



OPTIONAL
The first time the encrypted filesystem is mounted, the ownership of the root folder of the device will need to be changed to the current user as follows:
sudo chown userx:userx /media/disk -R
sudo chmod 755 /media/disk -R

sudo fdisk -l
sudo pvscan
sudo pvdisplay 
sudo pvdisplay /dev/sdx1

CREDITS
[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage)
[http://ubuntuforums.org/showthread.php?t=786756](http://ubuntuforums.org/showthread.php?t=786756)

---

### Post by t0p on 2011-02-04
I'm another Truecrypt user.  You can get it from [here]("http://www.truecrypt.org/downloads").

I think the problem with the licence is as described [here]("http://lists.freedesktop.org/archives/distributions/2008-October/000276.html"):

> 
Section III:

1. d. :  This provision requires distribution of source code if you
distribute "Your Product".  However, it says

  To meet this condition, it is sufficient that You merely include the
  source code with every copy of Your Product that You make and
  distribute . . . *provided that You make the copies available to the
  general public free of charge*; it is also sufficient that You merely
  include information . . . about where the source code can be freely
  obtained . . . with every copy of Your Product that You make
  and distribute . . . *provided that You make the copies available to
  the general public free of charge*. 

This is ambiguous, but the best reading of "the copies" seems to refer
to "every copy of Your Product that You make and distribute".  That
therefore means that if you distribute modified versions of TrueCrypt,
*you cannot charge for copies.  That is non-free*.**[my emphasis]**

So, because the Truecrypt licence does not allow you to charge for copies, the licence is incompatible with the GPL.  That makes it non-free; but not such that I won't use it.  I think Truecrypt is a great encryption tool, and it's a shame it can't be included in the repos.  Still, it's pretty easy to install yourself.  If you're not a Free software purist, I don't really see any reason not to use it.  If you *are* a Free software purist, I suggest you examine the software already running on your computer;I think there are a few programs included with Ubuntu that don't use the GPL.

---

### Post by Qwerty_ls on 2011-02-08
[QUOTE=vcrpcant;10426898]I believe you ment to thank septekin.

Vcrpcant, you're right, I meant Septekin (I've corrected my post)

Thank everybody for your help.

I'll try both Truecrypt and the Vcrpcant way.

---

