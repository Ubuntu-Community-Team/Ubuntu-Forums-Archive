---
title: "Extend LVM root partition on headless ubuntu 10.04 LTS"
date: 2012-04-02
forum: General Help
---

### Post by snobskidoo on 2012-04-02
Hi,

I'm currently running an ubuntu server 10.04 LTS headless and connecting via a combination of putty, webmin and occasionally VNC.   When I initially setup the box I used LVM and gave the root partition 4Gb and the swap 8Gb, however I now have used 3.5Gb on the root filesystem and would like to extend it.  Having read a number of threads and explanations I wonder whether someone could verify what the simplest and ideally safest way to achieve this is.  FYI here is my fdisk -l, df and lvs outputs:


root@server:~# lvs
  LV        VG     Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  documents server -wi-ao 100.00g
  media     server -wi-ao   1.37t
  music     server -wi-ao 300.00g
  osbackup  server -wi-ao  10.00g
  temporary server -wi-ao 200.00g
  xhomes    server -wi-ao  50.00g
root@server:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3844152   3591040    135948  97% /
none                   2023708       296   2023412   1% /dev
none                   2028560        24   2028536   1% /dev/shm
none                   2028560       316   2028244   1% /var/run
none                   2028560         0   2028560   0% /var/lock
none                   2028560         0   2028560   0% /lib/init/rw
/dev/mapper/server-xhomes
                      51606140    570336  48414364   2% /mounts/xhomes
/dev/mapper/server-documents
                     103212320  14650716  83318724  15% /mounts/documents
/dev/mapper/server-osbackup
                      10321208    154448   9957048   2% /mounts/osbackup
/dev/mapper/server-media
                     1444972436 788286024 627326284  56% /mounts/media
/dev/mapper/server-music
                     309637120 174266948 129078716  58% /mounts/music
/dev/mapper/server-temporary
                     206424760    191756 204135852   1% /mounts/temp
root@server:~# fdisk -l

Disk /dev/sda: 800.2 GB, 800166076416 bytes
255 heads, 63 sectors/track, 97281 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005cbe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         487     3905536   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             487        1459     7812096   82  Linux swap / Solaris
/dev/sda3            1460       97282   769691649    5  Extended
/dev/sda5            1460       97282   769691648   8e  Linux LVM

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001cb84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953513472   8e  Linux LVM
root@server:~#

In the list of LVS I cant see the root partition and the webmin config module doesn't appear to see it either.  

Would the best option be to plug in a live cd and attach a monitor and keyboard?

Many thanks for any help received x

---

### Post by galvatron408 on 2012-04-06
This isn't windows. You don't need to extend your drive.

Just add a new drive, format it and mount it to /opt/new

Then, move everything from /opt to /opt/new

last step, remount /opt/new to /opt

(Be sure nothing is running that is holding /opt prisoner)

---

