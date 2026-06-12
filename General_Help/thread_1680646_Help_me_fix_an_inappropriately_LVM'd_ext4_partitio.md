---
title: "Help me fix an inappropriately LVM'd ext4 partition"
date: 2011-02-02
forum: General Help
---

### Post by DDM on 2011-02-02
I got a new 2TB drive yesterday for my media center and decided to use LVM to add it to the other drive. I wanted to get rid of my often-slow XFS partition, so I copied about 1.3TB to the new drive after I had formatted it to ext4. Being quite stupid, I initialized the new drive (which now had everything on it) as a LVM physical volume. I was a little distracted by some unexpected company (and a few beers) so I can't exactly tell you what I did. 

So right now I'm using dd to create a disk image which won't be done for another day. In the meantime, I'm trying to figure out if I can simply undo the changes since I never formatted the drive.

If I try to mount the drive I get```
xbmc@htpc:~$ sudo mount /dev/sdb1  /media/2TB/
mount: unknown filesystem type 'LVM2_member'
```

Testdisk gives me this error```
                                                                                
Disk /dev/sdb1 - 2000 GB / 1863 GiB - CHS 243201 255 63                         
Current partition structure:                                                    
     Partition                  Start        End    Size in sectors             
                                                                                
                                                                                
Partition sector doesn't have the endmark 0xAA55
```
And finally```
xbmc@htpc:~$ sudo gpart -vv /dev/sdb1 

dev(/dev/sdb1) mss(512) chs(243201/255/63)(LBA) #s(3907024065) size(1907726mb)

* Warning: strange partition table magic 0x0000.
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


Begin scan...
```                  
And it hangs after that. 

I recovered a few important things with foremost, but it hasn't found everything. So if any of you experts can help me out I'd be indebted to you forever. Seriously.

PS: Is it safe to try to re-enable LVM on the drive?

---

### Post by DDM on 2011-02-03
I used GParted to remove the LVM flag and all is well.

---

