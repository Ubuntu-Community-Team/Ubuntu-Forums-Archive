---
title: "Trouble rebuilding Raid1 array"
date: 2011-10-19
forum: General Help
---

### Post by Clupus on 2011-10-19
Hello everyone, registered a while ago, but can't exactly say I've been an active member so far :popcorn:

I hope someone will be able to help me out here though:
I built a new computer, installed Ubuntu 11.10, and got into a little problem when I tried to move over a Raid1 array consisting of two 2Tb disks (**ext4**) from another computer.

Installed mdadm alright, but silly me used the mdadm --create to create a new array instead of mdadm --assemble (which I assume would've worked perfectly?). Anyway, created the new Raid1 array, got it started, but there's no filesystem on the array.

Tried mdadm --stop and mdadm --remove to delete the new array, then tried building a new array consisting of 1 disk + one missing, and then adding the second disk. Got the array started, but there's no filesystem on the array.

Tried deleting the new array again, now also deleting the superblocks with mdadm --zero-superblock on both disks. Got a little scared, ran a disk check and yes both disks are intact, there's an identical ext4 filesystem on both of them and all data are there (phew!).

Ok, so I've now got two identical disks, both with ext4 and filled with the exact same data. I figured there shouldn't be any problem simply creating a brand new Raid1 array now:
Tried again creating a new array, with 
```
sudo mdadm --create /dev/md0 --verbose --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```. 
Mdadm instantly started syncing the two devices, seems that went ok, and the array is now running. BUT it's running as /dev/md127 for some reason? /dev/md0 doesn't exist, even though in /etc/mdadm/mdadm.conf it says clearly:
```
# definitions of existing MD arrays
ARRAY /dev/md0 UUID=8bb0d80b:d5fe4508:2db7a00c:528770c9

```
Why it chooses to do this intrigues me, but here's my problem:

Trying to mount the array gives me: 
```
wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg | tail gives me
```
dmesg | tail
[    5.325318] Bluetooth: BNEP filters: protocol multicast
[    5.393102] init: plymouth-stop pre-start process (1665) terminated with status 1
[    6.902738] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    6.903058] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.439615] eth0: no IPv6 routers present
[  119.008404] EXT4-fs (md127): VFS: Can't find ext4 filesystem
[ 1632.922316] EXT3-fs (md127): error: can't find ext3 filesystem on dev md127.
[ 1632.946159] EXT2-fs (md127): error: can't find an ext2 filesystem on dev md127.
[ 1632.994094] EXT4-fs (md127): VFS: Can't find ext4 filesystem
[ 1639.039044] EXT4-fs (md127): VFS: Can't find ext4 filesystem
```

Any ideas anyone? [-o<

---

### Post by Clupus on 2011-10-20
Good news, got it fixed. Time consuming, but quite easy solution actually, just in case anyone ever gets in the same mess I'll just write down what I did here:

1. I did mdadm --zero-superblock on both disks, then did a disk check on them both so that I could mount them again. Made a new array with just one disk
```
sudo mdadm --create /dev/md0 --verbose --level=1 --raid-devices=2 missing /dev/sdc1
```
2. Made a new ext4 fs on the Raid1 array with mkfs.ext4.
3. Mounted the new array
4. Copied all the files from sdb1 to the array (with grsync)
5. Added sdb1 to the array with the --add command

Now after this was done it was just a matter of waiting for the array to resync, yet again. However, while previous resyncs went at >100MB/s it was now going at ~4MB/s. The solution to this I found here: [http://www.ducea.com/2006/06/25/increase-the-speed-of-linux-software-raid-reconstruction/](http://www.ducea.com/2006/06/25/increase-the-speed-of-linux-software-raid-reconstruction/) (Note: I had to do sudo -s -H in order to get permission to change the speed_limit_min).

Now, all is done and everything's working as it's supposed to (for now ;)).

---

