---
title: "File sharing without Samba?"
date: 2011-10-22
forum: General Help
---

### Post by notquitestr8t on 2011-10-22
I upgraded to 11.10. In order for my printer to work, I have to install a  386 version of libpopt0. This solves my printer problem, but then Samba fails. I've been told I don't need Samba but I don't see anything else in the forums for a file sharing solution. Any advise would be appreciated.

---

### Post by Jose Catre-Vandis on 2011-10-22
SSHFS, FTP or NFS - but for easy Windows sharing you are really going to want Samba

---

### Post by notquitestr8t on 2011-10-23
OK. So how do I enable NFS in Ubuntu?

---

### Post by Lars Noodén on 2011-10-23
Start here:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

You might try SSHFS first since there is such a low overhead in setting it up and running it.  If it meets your needs, then nothing further is needed.

---

