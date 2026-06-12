---
title: "After MAC TimeMachine Backup ..hfs 3tb hdd errors?"
date: 2011-08-11
forum: General Help
---

### Post by TechMansoor on 2011-08-11
I have a 3TB external hdd. Initially it worked fine on my ubuntu install(10.04). Upon doing reformatting the drive, as TimeMachine required, and doing a TimeMachine backup I'm not seeing an error message saying the drive is unmountable.

After doing a dmesg | tail, this is what I get:

mansoor@MansoorUbuntuWS:~$ dmesg | tail
[  261.868013]         00 00 00 00 40 50 
[  261.868021] sd 10:0:0:0: [sdc] ASC=0x4 ASCQ=0x1d
[  261.944610] sd 10:0:0:0: [sdc] Sense Key : Recovered Error [current] [descriptor]
[  261.944615] Descriptor sense data with sense descriptors (in hex):
[  261.944617]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[  261.944627]         00 4f 00 c2 40 50 
[  261.944632] sd 10:0:0:0: [sdc] ASC=0x4 ASCQ=0x1d
[  289.402303] CE: hpet increasing min_delta_ns to 15000 nsec
[  512.591698] hfs: volumes larger than 2TB are not supported yet
[  512.591702] hfs: unable to find HFS+ superblock
mansoor@MansoorUbuntuWS:~$ 



Any help woiuld be awesome..

Thanks

---

