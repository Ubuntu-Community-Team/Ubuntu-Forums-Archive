---
title: "problem wth truecrypt: i cannot mount my volume"
date: 2009-09-12
forum: General Help
---

### Post by ubunlilluz on 2009-09-12
hi,
today i've been trying to mount one hidden volume (with fs ext3) i created in an external hd.
Unfortunately this message appears:

mount: wrong fs type, bad option, bad superblock on /dev/mapper/truecrypt1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


i tried to run dmesg and i've sometime got:

Code:
drlillux@gcmagnum:~$ dmesg | tail
[ 7461.200989] sd 6:0:0:0: Attached scsi generic sg8 type 0
[ 7463.833976] EXT4-fs: barriers enabled
[ 7464.160086] kjournald2 starting.  Commit interval 5 seconds
[ 7464.160117] EXT4-fs warning: maximal mount count reached, running e2fsck is recommended
[ 7464.161127] EXT4 FS on sdh1, internal journal on sdh1:8
[ 7464.161134] EXT4-fs: delayed allocation enabled
[ 7464.161136] EXT4-fs: file extents enabled
[ 7464.237338] EXT4-fs: mballoc enabled
[ 7464.237350] EXT4-fs: recovery complete.
[ 7464.239231] EXT4-fs: mounted filesystem with ordered data mode.
drlillux@gcmagnum:~$

a sometime i've got:
```
drlillux@gcmagnum:~$ dmesg | tail
[ 2018.280094] Inbound IN=ppp0 OUT= MAC= SRC=69.162.105.98 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2049.516089] Inbound IN=ppp0 OUT= MAC= SRC=221.192.199.34 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2188.689942] EXT3-fs error (device dm-0): ext3_check_descriptors: Block bitmap for group 1536 not in group (block 1419208121)!
[ 2188.690239] EXT3-fs: group descriptors corrupted!
[ 2232.620092] Inbound IN=ppp0 OUT= MAC= SRC=69.162.105.98 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2438.132108] Inbound IN=ppp0 OUT= MAC= SRC=69.162.105.98 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2651.828185] Inbound IN=ppp0 OUT= MAC= SRC=69.162.105.98 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2670.944154] Inbound IN=ppp0 OUT= MAC= SRC=210.32.205.40 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=100 ID=256 PROTO=TCP SPT=6000 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2867.256133] Inbound IN=ppp0 OUT= MAC= SRC=69.162.105.98 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3084.936116] Inbound IN=ppp0 OUT= MAC= SRC=69.162.105.98 DST=151.30.187.165 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
drlillux@gcmagnum:~$ 

```

all other truecrypt volumes in this hd work fine and also outer volume of this volume works well
Somebody can help me, there're a lot of very important data in this volume
thanks

---

### Post by ubunlilluz on 2009-09-14
do nobody know as help me? :(

---

### Post by SecretCode on 2009-09-14
I don't see much discussion of Truecrypt on this forum - you might want to try forums.truecrypt.org

---

