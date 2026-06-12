---
title: "How to mount a NTFS partition?"
date: 2011-03-23
forum: General Help
---

### Post by sssecure on 2011-03-23
hello, im looking for a command for mounting an ntfs partition.
what i want to do is to put that command to the "after startup applications" option.
that's because that ntfs partition is my storage partition, i play steam games [win7 dualboot, thats why that partition is ntfs], download movies etc. 
in my places menu, its called 190GB Filesystem, and when i click it, it mounts up. 
but that means i have to click it everytime i boot up, because vuze can't locate the files if it isnt mounted. 

so whats the command, guys? :D
by the way : /media/7C1EE4E21EE49684 when its mounted

---

### Post by celldweller1591 on 2011-03-23
See this link - [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Morbius1 on 2011-03-23
Why not have it automount in fstab?

First, make sure you unmount the partition if it's currently mounted, then:

[1] Make a permanent home for the ntfs partition to live in:
```
sudo mkdir /media/Storage
```[2] Add a line to your /etc/fstab file:
```
UUID=7C1EE4E21EE49684 /media/Storage  ntfs    defaults,nls=utf8,umask=007,uid=1000,gid=46 0       0
```[3] Run the following command to test for errors and mount the new partition:
```
sudo mount -a
```

---

### Post by Hero1969 on 2011-03-23
You could also install PySDM (storage device manager) from the software center.  This gives you and easy GUI.

---

### Post by celldweller1591 on 2011-03-23
'ntfs config' would be a better and easy option to work with. Install it from Sfotware manager and run it, autoconfigure the newly found partitions if it shows up and tick 'Enable write support for external devices' and close it. Restart and everything wil be done.
[[IMG]http://img340.imageshack.us/img340/5142/47566076.th.png[/IMG]](http://img340.imageshack.us/i/47566076.png/)

---

### Post by alexmfm on 2011-03-23
don't know if it's PySDM what you are looking for but i use it to automount drives.
look for it on USC. it works for me.

update:just saw the post from hero1969. whatever he said works for me:)

---

### Post by Morbius1 on 2011-03-23
The very first question ntfs-config asks is if you want to enable write support for ntfs. Write support is enabled by default for ntfs as has been for some time. So you have to ask yourself why doesn't ntfs-config know that and what on earth does it do when you click yes.

As for PySDM, I always enjoy the challenge of fixing the mistakes that that utility has the propensity to make. 

The line in fstab that I posted is ( with the exception of my addition of uid=1000 - making you the owner) exactly what Ubuntu would have added to fstab had you asked it to do so during your initial install.

---

