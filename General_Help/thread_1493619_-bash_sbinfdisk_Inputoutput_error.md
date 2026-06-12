---
title: "-bash: /sbin/fdisk: Input/output error"
date: 2010-05-26
forum: General Help
---

### Post by pravindra.kumar on 2010-05-26
Dear All,

I have a LTSP server on Xubuntu9.04, till yesterday it was working fine but today morning it is giving some Input/output errors, some examples are following:-
-bash: /sbin/fdisk: Input/output error
-bash: /etc/profile: Input/output error
-bash: /root/.profile: Input/output error
even i am unable to open DHCP.conf file.
How can we fix this problem.
Thanks

---

### Post by dino99 on 2010-05-26
profile is complaining, have you installed some custom bash files ?

sudo dpkg --configure -a

will force a fsck on next boot:

sudo shutdown -F -r now

---

### Post by pravindra.kumar on 2010-05-26
After running the "dpkg --configure -a" it's giving I/O error:-
-bash-3.2# dpkg --configure -a     
dpkg: read error in configuration file `/etc/dpkg/dpkg.cfg': Input/output error
-bash-3.2# shutdown -F -r
-bash: /sbin/shutdown: Input/output error
-bash-3.2# 

And i run the dmesg command and it gave the following messages:-

[10589.103299] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793845, block=15171645
[10589.103398] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103408] end_request: I/O error, dev sda, sector 126931665
[10589.103418] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793752, block=15171639
[10589.103492] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103498] end_request: I/O error, dev sda, sector 108844401
[10589.103509] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3229855, block=12910731
[10589.103553] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103559] end_request: I/O error, dev sda, sector 126931337
[10589.103570] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793095, block=15171598
[10589.103612] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103622] end_request: I/O error, dev sda, sector 126931393
[10589.103633] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793215, block=15171605
[10589.103675] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103681] end_request: I/O error, dev sda, sector 126932721
[10589.103692] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3795865, block=15171771
[10589.103762] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103768] end_request: I/O error, dev sda, sector 126931649
[10589.103779] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793713, block=15171637
[10589.103866] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103876] end_request: I/O error, dev sda, sector 126931649
[10589.103887] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793722, block=15171637
[10589.103945] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.103951] end_request: I/O error, dev sda, sector 126931305
[10589.103967] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793029, block=15171594
[10589.104029] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104036] end_request: I/O error, dev sda, sector 126931401
[10589.104047] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793221, block=15171606
[10589.104120] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104130] end_request: I/O error, dev sda, sector 126931697
[10589.104140] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793820, block=15171643
[10589.104242] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104252] end_request: I/O error, dev sda, sector 126932753
[10589.104263] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3795934, block=15171775
[10589.104440] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104447] end_request: I/O error, dev sda, sector 126932753
[10589.104458] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3795923, block=15171775
[10589.104533] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104539] end_request: I/O error, dev sda, sector 126932945
[10589.104550] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3796319, block=15171799
[10589.104585] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104591] end_request: I/O error, dev sda, sector 126931297
[10589.104601] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793016, block=15171593
[10589.104645] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104655] end_request: I/O error, dev sda, sector 126931721
[10589.104666] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793863, block=15171646
[10589.104712] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104722] end_request: I/O error, dev sda, sector 126931769
[10589.104732] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=3793968, block=15171652
[10589.104764] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[10589.104770] end_request: I/O error, dev sda, sector 126931297

---

### Post by pravindra.kumar on 2010-05-26
Do i have to run fsck command on / partition?
or
Is there any way to fix the above errors?

---

