---
title: "Samba for backup purposes"
date: 2010-07-07
forum: General Help
---

### Post by cwscribner on 2010-07-07
Hi all.

I have a 2TB Seagate external drive.  I have two servers; one Windows 2003, one Ubuntu 9.04.  My thought was to set up a Samba share on the Ubuntu server that connects to the file sharing drive on the Windows server, and then backup the Samba share to the external hard drive.  Will this work?

**From a high level view**: I have 2 servers that need to be backed up to one external drive.  The drive can only be hooked to one server.  How do I do this?

---

### Post by bodhi.zazen on 2010-07-07
> **cwscribner said:**
> Hi all.

I have a 2TB Seagate external drive.  I have two servers; one Windows 2003, one Ubuntu 9.04.  My thought was to set up a Samba share on the Ubuntu server that connects to the file sharing drive on the Windows server, and then backup the Samba share to the external hard drive.  Will this work?

yes

**> From a high level view**: I have 2 servers that need to be backed up to one external drive.  The drive can only be hooked to one server.  How do I do this?

Share the drive, either with samba or nfs.

Create your backups any way you wish.

Move the backup files to the Seagate External Drive.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

