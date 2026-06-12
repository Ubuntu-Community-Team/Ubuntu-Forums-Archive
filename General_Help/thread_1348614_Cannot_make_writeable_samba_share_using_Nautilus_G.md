---
title: "Cannot make writeable samba share using Nautilus GUI"
date: 2009-12-07
forum: General Help
---

### Post by Soundman2 on 2009-12-07
Greetings.

I want users on my Ubuntu 9.10 (karmic) system to be able to share folders so that they can be read/written from their Windows box, using the simple GUI method to configure folder sharing, as described here: [http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems)

However, I have found that shares created this way are always read-only.  They remain read-only even if "Allow other people to write in this folder" is checked.  Even worse, that option actually does allow _other_accounts_ to write to the folder by changing its permission mask to be 777.

I do not want the folder to be writeable by _other_ users, but to be writeable by the user who owns it when mounted from a Windows XP box using their Linux account's user name & password.  I verified that the credentials Windows is using are correct by using ps to observe that the smbd process that gets forked during the mount is owned the the user who owns the folder being shared.

Of course, I can work around this problem myself by editing /etc/samba/smb.conf to manually create a writeable share.  However, this is a multi-user Ubuntu box, and I want the other users to be able to create their own writeable shares using the Nautilus GUI method.  Naturally, I've done lots of web searches but have come up dry on this.  Any help?

As a related question... when you use Nautilus to create a share, where does this configuration get written?  It's certainly not to smb.conf.

Thanks.

---

