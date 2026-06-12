---
title: "Network Sharing in Ubuntu"
date: 2012-02-09
forum: General Help
---

### Post by plasticcorndog on 2012-02-09
In one or two sentences, how does Ubuntu's network file sharing work?  
Can I share files to a Windows computer?  To a blu ray player?  Do I have to run a program to have it share files or does it do it automatically?  Thank you!

---

### Post by dannyboy79 on 2012-02-09
the easiest way would be to setup a samba server (SMB protocol). using shared security which is not require user level authentification. There's guides within the tips and tutorial section. It can share files to pretty much anything using wither SMB, FTP, NFS, or UPnP (TM) A/V & DLNA Media Server.

---

### Post by raja.genupula on 2012-02-09
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

hope that helps

---

### Post by Morbius1 on 2012-02-09
Open Nautilus
Right Click on a folder you own ... say Documents for example.
Select "Sharing Options"
If you don't have Samba installed it will ask you if you want it to install Windows Networking - you do.
Then click on all three options.
It will ask you if you want it to modify permissions - you do.

You just created a Samba guest accessible share of your Documents folder in a proces that is not coincidentally not unlike the way you would create a WinXP "Simple Share".

That's not one sentence but it's the best I can do.

---

