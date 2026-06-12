---
title: "Calling File System Guru's...help!"
date: 2011-07-23
forum: General Help
---

### Post by Al Grant on 2011-07-23
Hi All,

I am messing around with NTFSCLONE and some other NTFS tools in Ubuntu.

What I am trying to achieve is the ability to write a NTFS image of a XP machine to a disk and then boot that disk.

I don't want to use dd cause its slow, and does the whole disk.

I am running into a problem however in my methodology and I hope someone more knowledgeable than me here can help.

Progress so far:

1. Install XP on a spare PC.

2. Remove hard disk and connect to my Ubuntu box.

3. Clone XP partition (sdb1) with NTFSCLONE:

```

sudo ntfsclone --save-image --output /home/al/XP_physical_OEM_SP2.ntfsclone /dev/sdb1

```

4. Erase the disk. Zero fill the sucker to make sure its blank. Now set about recreating things on the disk.

5. Create partition with fdisk: n for new primary partition. Starting at sector 63 (thats same as what is was), mark bootable and set type to 07. w to write it to disk and then run partprobe.

6. 
```

sudo ms-sys -m /dev/sdb

```

7. Put partition data for XP back with;

```

sudo ntfsclone --restore-image --overwrite /dev/sdb1 /home/al/XP_physical_OEM_SP2.ntfsclone

```

8. Attempt to boot the disk and I get:

Error loading operating system 

Right after POST finishes.

I have done some experimenting and tend to think that I am getting something wrong in either MBR or part table as I would get Operating System not found?

I have used dd to take the first 512b from the disk when it working, before I zero fill the drive

```

al@al-ubuntu:~$ file mbr1.bin
mbr1.bin: x86 boot sector, Microsoft Windows XP MBR, Serial 0x8d80fdb8; partition 1: ID=0x7, active, starthead 1, startsector 63, 39085137 sectors, code offset 0xc0

```

And the again took a copy of the first 512b after the ntfsclone operation:

```

al@al-ubuntu:~$ file mbr3.bin
mbr3.bin: x86 boot sector, Microsoft Windows XP MBR; partition 1: ID=0x7, active, starthead 1, startsector 63, 39102273 sectors, code offset 0xc0
al@al-ubuntu:~$ 

```

The only difference I can see is the 'serial number' (not sure what it is or does?) and the end sectors - which I dont think should effect the ability to boot?

Anyone able to please help?

Thanks

-Al

---

### Post by Al Grant on 2011-07-23
Here is the mbr's in hex too:

```

al@al-ubuntu:~$ hexdump -C -s 512 mbr1.bin
00000200  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000210  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000220  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000230  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000240  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000250  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000260  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000270  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000280  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000290  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000002a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000002b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000002c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000002d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000002e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000002f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000300  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000310  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000320  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000330  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000340  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000350  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000360  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000370  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000380  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000003b0  00 00 00 00 00 2c 44 63  b8 fd 80 8d 00 00 80 01  |.....,Dc........|
000003c0  01 00 07 ef ff ff 3f 00  00 00 51 64 54 02 00 00  |......?...QdT...|
000003d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000003f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000400
al@al-ubuntu:~$ 

```

And the ntfsclone one:

```

al@al-ubuntu:~$ hexdump -C -s 512 mbr3.bin
00000200  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000210  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000220  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000230  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000240  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000250  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000260  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000270  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000280  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000290  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000002a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000002b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000002c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000002d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000002e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000002f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000300  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000310  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000320  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000330  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000340  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000350  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000360  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000370  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000380  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000003b0  00 00 00 00 00 2c 44 63  00 00 00 00 00 00 80 01  |.....,Dc........|
000003c0  20 00 07 3f e0 ff 3f 00  00 00 41 a7 54 02 00 00  | ..?..?...A.T...|
000003d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000003f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000400
al@al-ubuntu:~$ 


```

I suck at reading hex.

---

### Post by Al Grant on 2011-07-29
I solved it and have posted a tutorial here for anyone interested:

[http://www.youtube.com/watch?v=UDM39Vo8Z0M](http://www.youtube.com/watch?v=UDM39Vo8Z0M)

The key is in copy the disk geometry in *CHS* as well as getting the size right in sectors!

---

