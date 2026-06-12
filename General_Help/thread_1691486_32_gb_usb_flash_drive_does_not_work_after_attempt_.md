---
title: "32 gb usb flash drive does not work after attempt on formating"
date: 2011-02-19
forum: General Help
---

### Post by arnetheman on 2011-02-19
I bought a cheap 32 gb usb flash drive in China which worked just fine on Ubuntu.
However, when I attempted to tranfer som files to a Windows7 computer I got a message saying I had to format the flash drive before using. I did this, but the formating failed.
When inserting the flash drive in Ubuntu again it was it was detected but unable to mount. I tried to format it again using GParted, but again it was unable to format.

Now Ubuntu won't detect the flash drive when inserting. Windows7 does detect, but I get the message saying it needs formating.

What to do?

---

### Post by jerrrys on 2011-02-21
gparted shouldn't have any problem formatting a usb, but if windows is happy then stick with ntfs.  ubuntu can handle ntfs, maybe all you need is some tools

[ATTACH]184035[/ATTACH]

---

### Post by seawolf167 on 2011-02-21
In Ubuntu, you'll want the following 2 programs to format NTFS:

```
sudo apt-get install gparted
sudo apt-get install ntfsprogs
```Then use Gparted like normal to format/resize/whatever the NTFS partition.

---

### Post by mshenrick on 2011-02-21
Post the output from 'sudo fdisk -l'

also, does the drive have any special features, eg. U3? these are good on windows but can interfere with normal operation on linux.

---

### Post by mshenrick on 2011-02-21
the simplest answer is probably to format on windows. linux can read it

---

