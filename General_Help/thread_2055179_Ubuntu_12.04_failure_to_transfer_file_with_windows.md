---
title: "Ubuntu 12.04 failure to transfer file with windows 7"
date: 2012-09-08
forum: General Help
---

### Post by 1DoLittle on 2012-09-08
I have a workgroup network with a Windows 7, XP, Ubuntu 12.04  computers, and a Canon printer.
Problem is the Ubuntu will not read files on W7 but W7 will transfer files both ways with Ubuntu. The Ubuntu works on the internet fine and prints wireless properly.

I did not mount any drives because I don't use this type of function very often.

The Ubuntu recognized both the W7 and XP computers, but will not open up the shared files.

---

### Post by critin on 2012-09-08
> 
The Ubuntu recognized both the W7 and XP computers, but will not open up the shared files. 	

What is the message you get when you click on Win7 file?  Sounds like a permission is missing somewhere.

---

### Post by 1DoLittle on 2012-09-08
Ubuntu displays all nodes on the network, but will not open either the W7 or XP computers. On the same display with the computers is the printer, which works properly.

---

### Post by critin on 2012-09-08
You should get a message of some kind if the files won't open.

You created a workgroup in win7.   When you open Home folder in ubuntu, you can see --Network--Browse Network--at the bottom of the left menu?  When you click Browse Network, the Windows Network icon shows?  When you click on Win Network, the Workgroup icon shows?  When you click on Workgroup, either a password is asked for, or the windows machines show?

---

### Post by critin on 2012-09-08
Don't forget to restart all machines after adding to the workgroup.

(As a test) I just now added a new ubuntu install to Win workgroup:   I went to windows, got the Workgroup password, entered it into the popup when clicking the win icon, chose 'remember forever', then it asked for the windows password,  then it let me in.  I didn't do anything to ubuntu.  I can share both ways.

---

### Post by 1DoLittle on 2012-09-08
All the menus you mention work properly, but the icons for the computers and printer are not correct. When clicking on any of the computers, just a long wait for nothing to show. 
Looking at properties on one of the computers, under the permissions tab this statement is displayed "The permissions of 'smb' could not be determined"
I have not located a reason for this statement.

---

### Post by critin on 2012-09-08
> **coalpile said:**
> All the menus you mention work properly, but the icons for the computers and printer are not correct. When clicking on any of the computers, just a long wait for nothing to show. 
Looking at properties on one of the computers, under the permissions tab this statement is displayed "The permissions of 'smb' could not be determined"
I have not located a reason for this statement.

Okay.  Find the ubuntu files shared with Windows and click on Permissions, choose your permissions and shares.  At that point it will ask if you want to add shares, say yes and it will add the 'smb' shares.  (That stands for Samba.}  Also check access to read and write in that same area, next page.  

With Folders, click on Share, then go inside the folder and fix the permissions (for files contained inside this folder)  the same way as you did files. (above)

On windows shares, and ubuntu, I always choose 'share without password' so I can get into the files easier.  If you need them locked, you won't.  I just wanted to say you can share without password if you wanted to.  Enter it once and have it remembered 'forever'.  lol


Be sure to share in Windows too.  Those options are in the Homegroup section.  Network and Sharing Center.  Advanced sharing settings.  Do this for all networks, including public.


Restart after doing all this.  You may have to enter the Homegroup password.  I did on 12.04, I did not have to on earlier versions.

---

