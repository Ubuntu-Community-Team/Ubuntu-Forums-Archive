---
title: "File and directory ownership issues"
date: 2012-05-17
forum: General Help
---

### Post by ZombeApocalips on 2012-05-17
Hi, all.  Very new Ubuntu user here (in the sense that my level of expertise is nonexistant).  I have actually used Ubuntu for some time, but that was basically just for browsing the web and as a media center running boxee.  Which brings us to my issue.

I recently changed an older rig I've been using primarily as a file server and streaming media server for some time using Windows XP.  I was having serious performance issues with a streaming media server, and changed over to Ubuntu 11.04 to get the performance boost over windows.  I have not been disappointed in that regard.  I'm running into issues trying to set up a Samba share on an external drive, which will prevent me from hosting the media on this machine and using my boxee media center pc (running windows xp for now) in the other room.

The issue I'm having is that I can't set a folder on the external drive to be shared.  I'm getting an error message stating that I'm not the owner of the file/directory.  I'm the only user.  I have already installed ntfsmount and used this to change some permissions for my media server program.  I understand that I'm supposed to add:

usershare owner only = false

into the [global] section of smb.conf, however I can't save over this file because the error somes up saying I'm not the owner of the file.  My confusion is how can the ONLY user (set as an administrator) not own the external storage or any file? I have tried creating a new directory on the external HDD but can't share that either, getting the same message about not being the owner.  Of the directory I just created.  I'm confused.  It's an NTFS HDD if that makes any difference (somehow I'm sure it does).  Please assume that I have zero knowledge of anything other than the GUI in Ubuntu, and little knowledge of the GUI at that.

Thanks in advance for any help anyone can offer.  I would certainly settle for a line by line how-to, but bonus points for helping me actually understand what I'm doing.  I would like to be as familiar with Linux one day as I am with Windows today.

---

### Post by ZombeApocalips on 2012-05-18
Found it myself after searching more.  In case anyone else is having this problem, open the terminal and use:

gksudo gedit /etc/samba/smb.conf
and add the above mentioned string.

---

### Post by 2F4U on 2012-05-18
Nice you found the solution. Could you mark your post as solved then?

---

