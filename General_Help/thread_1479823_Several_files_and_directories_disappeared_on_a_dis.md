---
title: "Several files and directories disappeared on a disk"
date: 2010-05-11
forum: General Help
---

### Post by JF89 on 2010-05-11
Hello,
 

 Can you help me to identify my ubuntu bug?
 

I tried to unzip a file dowloaded with a torrent , but I failed access to the  volume where I registered it .

There is only 6.6 Go  that appears in the files browser out of 46 Go stored.

I couldn't have access to the volume ,soo, I put it off.

Since that , I lost access too 40 Go datas.


 Can you tell me if a software exists, to find out all the directories and files lost ?


 

 

 I tried testdisk , but the résult was good.

 When trying : sudo testdisk /dev/sdb
The résult was:

* HPFS - NTFS              0   1  1  9728 254 63  156296322 [DATA]
Structure: Ok

Résult for: list files option
dr-xr-xr-x     0     0         0 15-Apr-2007 09:51 .
dr-xr-xr-x     0     0         0 15-Apr-2007 09:51 ..
-r--r--r--     0     0    684118  5-Apr-2007 15:29 FWManager.exe


But when I tried to send a ls command  the résult was:  
 
ls: reading directory .: Input/output error

jf@jf-desktop:/media/DATA/Sauvegarde$ 


Do I have to send the command :   Write TestDisk MBR code to first sector , with testdisk?


Is the Input/output error a  hard problem?

Regards

---

