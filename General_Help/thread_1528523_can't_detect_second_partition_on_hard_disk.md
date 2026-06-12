---
title: "can't detect second partition on hard disk"
date: 2010-07-10
forum: General Help
---

### Post by satanic-yobbo on 2010-07-10
i need a little help to get Lucid to detect a secondary partition on a 320gb hdd... i have a 1tb sata drive partitioned into smaller drives (one of which hold lucid install) , all of these are detected properly .. a 120gb ide that is fine and a 320 gb sata that holds a windows vista system on one partition and on the second partition it holds media so as not to clog the windows C:or lose data if it(or rather when ) it crashes .. my problem is that i cannot detect let alone mount this second partition in lucid even though it works fine and is detected as normal in windows. any help would be greatly appreciated as i have no idea why it is doing this .

---

### Post by garvinrick4 on 2010-07-10
When you run: (Lower case L in both)
```
sudo fdisk -l
``````
sudo blkid
```What is the results?

---

### Post by satanic-yobbo on 2010-07-10
i ran them and the results are as follows 


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18421841

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803404+   5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         637     5113844    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2             638       69911   556436875    7  HPFS/NTFS
/dev/sdb3           69911      107969   305704961    f  W95 Ext'd (LBA)
/dev/sdb4          107970      121601   109499040    7  HPFS/NTFS
/dev/sdb5           69911      107969   305704960   83  Linux

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064df8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       25493   204771328    7  HPFS/NTFS
/dev/sdc2           25494       38912   107788117+   f  W95 Ext'd (LBA)
/dev/sdc5           25494       38912   107788086    7  HPFS/NTFS
aj@aj-desktop:~$ sudo blkid
/dev/sda1: UUID="2ded9685-9bc8-4471-8f1a-212192e5eeb3" TYPE="ext4" 
/dev/sda5: TYPE="swap" 
/dev/sdb1: LABEL="dads music" UUID="3E82E16E82E12B5B" TYPE="ntfs" 
/dev/sdb2: LABEL="Everything" UUID="7E8CEEC18CEE72D7" TYPE="ntfs" 
/dev/sdb4: LABEL="stuff" UUID="62DC5D8DDC5D5BFB" TYPE="ntfs" 
/dev/sdb5: UUID="3d753b8c-ffbc-4f1b-9485-a1f59bc7985c" TYPE="ext3" 
/dev/sdc1: UUID="72A02D0FA02CDB7D" TYPE="ntfs" 
/dev/sdc5: LABEL="detected" UUID="EE687E25687DECA9" TYPE="ntfs" 

the disc at the end (320 gb ) is the one that i cannot detect the second partition on

---

### Post by WorMzy on 2010-07-10
So is the media partition the one with the label "detected"?

If so, what message do you get if you run 'sudo mount -t ntfs /dev/sdc5 /mnt'

---

### Post by satanic-yobbo on 2010-07-10
yeah that is the media i am trying to mount . i labelled it detected so i know which one it is a was looking for and when i run

 sudo mount -t ntfs /dev/sdc5 /mn i get the message 

fuse: failed to access mountpoint /mn: No such file or directory

---

### Post by WorMzy on 2010-07-10
There's a 't' at the end of mnt. ;)

---

### Post by satanic-yobbo on 2010-07-10
ok .. after i ran this code ...properly ..:oops: i got no error or message of any kind and it seemed like there was no reaction so i re ran it again and it tells me now 
fuse: mount failed: Device or resource busy .. seems like it is trying to do something from he sound of the hdd but there is still nothing showing in "places" or "computer " should i do a restart and run the code again and try a little patience and wait for it this time ?

---

### Post by WorMzy on 2010-07-10
No, it looks like it mounted fine. Open nautilus (the file browser) and navigate to /mnt (you can press Ctrl+L while in nautilus to bring up the address bar, just type /mnt there and press enter), your files should be there.

Now, assuming it all looks fine and it mounted with no problems, you can set the partition to automatically mount every time you boot by adding an entry for it in /etc/fstab.

To edit fstab run
```
gksu gedit /etc/fstab
```
At the bottom of the file, on a _new line_ add the following:
```
UUID=EE687E25687DECA9 /media/[COLOR="Red"]share[/COLOR] ntfs user,uid=1000,gid=1000,umask=002,exec,rw 0 0
```

Do not modify any other part of this file, unless you know what you're doing; but feel free to change the word in red to something more suitable if you want.

Save and close the file.

Finally, create the directory that you're going to mount it in with:
```
sudo mkdir /media/[COLOR="Red"]share[/COLOR]
```
Making sure that the directory you create is the same as you wrote in fstab.

---

### Post by satanic-yobbo on 2010-07-10
ok .. just ran those last codes and it all looks great .. i will now re boot and see if it all works like i hope and post back results in a few mins .. thank you for your help

---

### Post by satanic-yobbo on 2010-07-10
everything is perfect now .. all as it should be .. thank you very much for your help and time ... all mounts perfectly on startup and detects perfectly ... thank you very much once again :D :D

---

### Post by WorMzy on 2010-07-10
No problem. :)

---

