---
title: "Multiple drive items (icons) in nautilus"
date: 2011-02-26
forum: General Help
---

### Post by wolterh on 2011-02-26
I have a "Storage" partition in my hard drive which I have labeled as such and added to fstab. This is my fstab file:
```

proc      proc                                       /proc           proc  defaults                               0  0  
UUID=659ebc81-0dbb-476a-9847-c78639a7e97a  /               ext4  errors=remount-ro                      0  1  
UUID=eab80bfb-b2d0-4c26-bac1-5495d46b4bac  none            swap  sw                                     0  0  
UUID=5BA0A9BB3FB5F7AF                      /media/Storage  ntfs  uid=1000,gid=1000,users,auto,exec,rw   0  0 
/media/Storage/Home/Wolter/Portal	/home/wolter/Public/Local none defaults,bind 0 0
UUID=b13c729b-2c9e-46a8-9780-2adb1cc97236 /home ext3 defaults,user_xattr 0 2

```

The problem is that when I open up nautilus and click the Computer icon in the toolbar (which gives the fake computer:/// address) I see two items referring to my Storage partition:
 * Storage (which appears to be of "unknown type" in the properties).
 * 500 GB Hard Disk: Storage (which is the one that works).

As you may have guessed, I want to get rid of the first item, but I have no clue on how to do it. Suggestions?

---

### Post by wiggly81 on 2011-02-26
looks to me that either you double posted your fstab file or you have all drives / partitions listed twice in it?

---

### Post by wolterh on 2011-02-26
Oops, I pasted twice. My actual fstab file does not look like that; I already corrected my post, thanks for noticing!

---

### Post by SteveyDevey on 2011-03-03
I'm actually having a similar problem, and I'm interested to hear if anyone has any advice where to look for a solution.

My fstab doesn't have multiple copies of the drives listed, but since I've got 4 partitions mounted, I see them all twice. 

I'm willing to bet this was started when trying to get ubuntu to auto-mount the ntfs partitions with proper permissions (which took a few tries), but I can't seem to find what is making it think there should be two copies of each. :(

---

### Post by xDigitalStealthx on 2011-03-06
I am having the exact same issue. Here's my story. I started with two drives, both of which were originally ntfs drives that were once successfully mounted and sharing files not only across the network, but to my xbox as well, but only after much tweaking. 

Currently, both drives are formatted using a GUID partition table, ext4, and have a only 1 partition each. Each drive has its own entry in /etc/fstab as follows:

```
# Storage 250GB /dev/sdb1
UUID=9ef74a0e-ac8e-4cd0-bc0f-96869dd5376c /media/Storage ext4 defaults,user,noexec,nosuid,rw 0 0

# Media 200GB /dev/sdc1
UUID=63231c7d-5f6b-4ee9-8e7b-b4769e0b9408 /media/Media ext4 defaults,user,noexec,nosuid,rw 0 0
```

I manually created two files in /media as follows:

```
:~$ sudo mkdir /media/Media
sudo mkdir /media/Storage
sudo chown zac -R /media/Media
sudo chown zac -R /media/Storage

```

Each drive is listed twice in nautilus and can be mounted and unmounted by me. Also, I cannot share any folders on the drive. When I attempt to share the folders through nautilus, i get the following error:

'net usershare' returned error 255: net usershare add: failed to add share music. Error was Operation not permitted

I think this problem has something to do with ubuntu automatically creating folders in the /media directory when there appears to be a hot-pluggable drive present, but it could also be something as simple as changing a setting in nautilus. Either way, any help would be greatly appreciated.

---

### Post by Insperatus on 2011-08-28
Bump

I'm having this problem too.  Edited fstab to automount an ntfs partition.  Setting the automount added another icon - now it shows twice in nautilus.

Ubuntu 11.04 64-bit

---

### Post by tyler.olpin on 2011-09-13
Bump

---

### Post by eliezer.souzareis on 2011-11-06
bump friend, a huge bump
this bug seems to be te same as 'bug#251991' but they already corrected it.
 I am using Ubuntu 11.04 w/ gnome

---

### Post by wolterh on 2011-11-07
Yes the problem seems to be gone for me too. I stopped seeing it after I upgraded to Ubuntu 11.10 though.

---

### Post by stevepoppers on 2012-01-21
Seeing this problem on 11.04. Only shows up when I use label or uuid in fstab. Using the /dev/sdx# "fixes" it, but that often changes during reboot.
If I have to upgrade to 11.10 to fix it, I won't be using Ubuntu for long. I am NOT using Unity.

---

