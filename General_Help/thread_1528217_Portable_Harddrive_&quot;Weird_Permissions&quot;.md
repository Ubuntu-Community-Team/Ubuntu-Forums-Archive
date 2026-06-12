---
title: "Portable Harddrive &quot;Weird Permissions&quot;"
date: 2010-07-10
forum: General Help
---

### Post by lynx_hanan on 2010-07-10
HI everyone,

A few days back i lend my Portable Hard-drive (Wester Digital) to a friend. He used it for transferring some of his Data back from his Office PC. After i got my Hard-drive back i plug into my Laptop (Ubuntu 10.04) it detects the Hard-drive. Mounts it. But only shows a few of the folders. These are my messages logs
> 
Jul 10 20:21:29 ubuntu kernel: [ 3113.264272] usb 2-3: new high speed USB device using ehci_hcd and address 9
Jul 10 20:21:29 ubuntu kernel: [ 3113.398907] usb 2-3: configuration #1 chosen from 1 choice
Jul 10 20:21:29 ubuntu kernel: [ 3113.399353] scsi10 : SCSI emulation for USB Mass Storage devices
Jul 10 20:21:34 ubuntu kernel: [ 3118.397967] scsi 10:0:0:0: Direct-Access     WD       My Passport 070A 1030 PQ: 0 ANSI: 4
Jul 10 20:21:34 ubuntu kernel: [ 3118.399209] scsi 10:0:0:1: CD-ROM            WD       Virtual CD 070A  1030 PQ: 0 ANSI: 4
Jul 10 20:21:34 ubuntu kernel: [ 3118.400723] scsi 10:0:0:2: Enclosure         WD       SES Device       1030 PQ: 0 ANSI: 4
Jul 10 20:21:34 ubuntu kernel: [ 3118.402042] sd 10:0:0:0: Attached scsi generic sg2 type 0
Jul 10 20:21:34 ubuntu kernel: [ 3118.406345] sr1: scsi3-mmc drive: 51x/51x caddy
Jul 10 20:21:34 ubuntu kernel: [ 3118.406561] sr 10:0:0:1: Attached scsi generic sg3 type 5
Jul 10 20:21:34 ubuntu kernel: [ 3118.406653] ses 10:0:0:2: Attached Enclosure device
Jul 10 20:21:34 ubuntu kernel: [ 3118.406712] ses 10:0:0:2: Attached scsi generic sg4 type 13
Jul 10 20:21:34 ubuntu kernel: [ 3118.408234] sd 10:0:0:0: [sdd] 487024640 512-byte logical blocks: (249 GB/232 GiB)
Jul 10 20:21:34 ubuntu kernel: [ 3118.410084] sd 10:0:0:0: [sdd] Write Protect is off
Jul 10 20:21:34 ubuntu kernel: [ 3118.412974]  sdd: sdd1
Jul 10 20:21:34 ubuntu kernel: [ 3118.471847] sd 10:0:0:0: [sdd] Attached SCSI disk
Jul 10 20:21:35 ubuntu kernel: [ 3118.967119] UDF-fs: Partition marked readonly; forcing readonly mount
Jul 10 20:21:35 ubuntu kernel: [ 3118.979497] UDF-fs INFO UDF: Mounting volume 'WD SmartWare', timestamp 2009/10/15 02:49 (112c)




I can only view One of Folder in GUI
and in terminal i can see all but the permissions dont make sense
> 

drwx------  1 sufi sufi     16384 2010-07-10 19:59 .
drwxr-xr-x 10 root root      4096 2010-07-10 20:13 ..
drwx------  1 sufi sufi      4096 2010-04-27 12:31 Hilal-data
-rwxrwxrwx  3 sufi sufi 792336928 2010-06-28 14:56 LV2009_ENG_32.exe
d?????????  ? ?    ?            ?                ? Matlab 2010
d?????????  ? ?    ?            ?                ? Multimedia & Games
d?????????  ? ?    ?            ?                ? RECYCLER
d?????????  ? ?    ?            ?                ? SEOS_6_1_5_4
-?????????  ? ?    ?            ?                ? SEOS_6_1_5_4.zip
d?????????  ? ?    ?            ?                ? Softwares
d?????????  ? ?    ?            ?                ? System Volume Information
drwx------  1 sufi sufi         0 2010-07-10 19:57 .Trash-1000
d?????????  ? ?    ?            ?                ? WE WERE SOLDIERS[MEL GIBSON][699MB DVDRIP][ENG]-JOCKTHERIPPER
d?????????  ? ?    ?            ?                ? xilinx



When i switch to my Windows 7 Install i get a prompt to Format the disk as it is unformatted.

My Question!!! is there a way i could recover this Data. I really need the softwares folder :-( i can live without rest.

---

### Post by lynx_hanan on 2010-07-10
Also i forgot to mention 

root@ubuntu:/media/temp# cd Matlab\ 2010 
-bash: cd: Matlab 2010: No such file or director

i cannot Open or Delete these files even with root

---

