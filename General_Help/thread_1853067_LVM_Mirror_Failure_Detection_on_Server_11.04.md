---
title: "LVM Mirror Failure Detection on Server 11.04"
date: 2011-10-01
forum: General Help
---

### Post by kurrazyman on 2011-10-01
I have a test setup: -

Server 11.04
LVM2 (installed from Repo)
/dev/sda: 8GB SSD with OS installed (sda1=Root, sda2=swap, sda3 = LVM)
/dev/sdb: 160GB PATA with 200M LVM partition (sdb1)
/dev/sdc: 160GB PATA with 200M LVM partition (sdc1)

I'm trying to test LVM Mirroring before using it on my actual server and all I've done is create a mirrored LV (lv01) within a VG that has three block devices in it:-

sda3 (For Mirror log file)
sdb1 (200M lv01 Leg 1)
sdc1 (200M lv01 Leg 2)

Output from 'lvs -a -o +devices': -

LV              VG   Attr   LSize   Log       Copy% Devices
lv01            vg01 mwi-a- 196.00m lv01_mlog 100%  lv01_mimage_0(0),lv01_mimage1(0)
[lv01_mimage_0] vg01 iwi-ao 196.00m                 /dev/sdb1(0)
[lv01_mimage_1] vg01 iwi-ao 196.00m                 /dev/sdc1(0)
[lv01_mlog]     vg01 lwi-ao 4.00m                   /dev/sda3(0)

And all works well until I try and simulate a HDD failure; from what I have read when a failure occurs and a write is made to the LV the LV mirror will be converted to a linear LV and happily carry on.

On Ubuntu Server 11.04 this switch over to a linear LV doesn't happen, the only message that appears from device-mapper upon failure is 'Mirror write failed from 251:1. Trying alternative device.' and output from 'lvs -a -o +devices' becomes: -

Couldn't find device with uuid xxxxxx.......
LV              VG   Attr   LSize   Log       Copy%  Devices
lv01            vg01 mwi-a- 196.00m lv01_mlog 97.96% lv01_mimage_0(0),lv01_mimage1(0)
[lv01_mimage_0] vg01 iwi-ao 196.00m                 unknown_device(0)
[lv01_mimage_1] vg01 iwi-ao 196.00m                 /dev/sdc1(0)
[lv01_mlog]     vg01 lwi-ao 4.00m                   /dev/sda3(0)

I then get a message every 120s or so 'INFO: task kjournald:977 blocked for more than 120seconds' which I guess is related to the failed write attempt.

I have been trying to find a solution to this for hours but haven't had much luck (tried installing all the devmapper packages in the repo), one thing I did notice is that lvm.conf points to a module 'libdevmapper-event-lvm2mirror.so' that is supposed to deal with monitoring failures but this isn't on my install anywhere.

Hopefully someone can help or I'll have to go back to mdadm.

Many Thanks in advance!

---

### Post by kurrazyman on 2011-10-03
Bump.....There must be someone out there that knows something about LVM or can point me in the direction of someone that does please

---

