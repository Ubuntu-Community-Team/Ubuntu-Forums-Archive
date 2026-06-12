---
title: "Samba 3 smb share automount issue within Ubuntu (Unless root)"
date: 2010-11-23
forum: General Help
---

### Post by efurlan on 2010-11-23
So after attempting to research on my own (And I might have the answer just need to explained or expanded upon), I have attempted to auto mount shares onto the Ubuntu environment using fstab while in root access. I have one server that is a Samba share (zentyal / ebox) and windows server 2003 (both are using SMB and 2003 has a dummy NFS share setup).

So here's the issue: the drives mount onto the desktop fine every time. However, Opening the actual drives outside root / super user causes various issues. The drives won't open for some users, and some will open and gives a INPUT/OUTPUT error when actually trying to open files on the drive. However, this does not happen with root at all. 

When I try to change permissions of the "Share" which is in the media area, Ubuntu will either say I don't have permission to change it, or I have to unmount and then it will act as if it's successful, but won't actually change the owner and won't let me change the group... I also can't change the selection for file access permission... it stays at -- when trying. This is quite frustrating since sometimes I am able to change aspects of the permissions. Again, when I automount the drive it's using the administrative login information for the server... so it seems to be an ubuntu side issue mainly...

So simple solution or strange situation? 

FSTAB shares are set up the following way:

//servername/sharename  /media/mountname  cifs  username=myusername,password=mypassword  0  0

again flawless as long as I'm in root, however it's a headache trying to change the permissions within Ubuntu for the share / auto mount

---

