---
title: "Samba &amp; Ubuntu 10.04 Server - **Newbie**"
date: 2010-05-04
forum: General Help
---

### Post by LeoCortes on 2010-05-04
Hello Gents,

Disclaimer: I am 100% new to Linux, coming across "sudo", "pico", "/etc",  "/home" for the first time ever and having to face it via command line with the Server version. Also, before posting this, I have done my  research as in 12 (almost consecutive) hours of it, so please do not  assume I am a lazy person who didn't even give it a try. All in all,  please be very descriptive in your replies. Don't tell me to "check  umask settings" without explaining how to accomplish it. Thanks!!

So here's the deal: I have a small SOHO (Small Office/Home Office)  network served by Windows Home Server and I thought it was time to give  Linux a try and clearly, Ubuntu was the way to go here. First I had a  hard time figuring out the whole partitioning thing... I have 3 HDs in  the server: 1x160 Gb and 2x 1.5Tb (identical). After a while, this is  what I came up with:
sda: 60Gb swap, 40 Gb root, 60 Gb /usr
sdb and sdc: LVM 3 Tb /home

I installed Server 10.04 with LAMP, OpenSSH and Samba. I managed to  install phpmyadmin and LAMP is working flawlessly. My issue is with  Samba.

I have tried **several** adjustments to the smb.conf file in accordance  to several texts found in this forum and elsewhere to no avail. The  issue I am experiencing relates to  permissions, I believe. Every time I try to  write to a folder other than the user's own folder from a Windows  machine, I get this error: "You need permission to perform this action".

Here's the environment:

==============
Ubuntu Server:

/home/supershare[INDENT]/supershare/company
[/INDENT][INDENT]/supershare/family
[/INDENT]/home/public[INDENT]/public/entertainment
[/INDENT]Unix accounts | passwords | group:
user1 | pass1 | workgroup
user2 | pass2 | workgroup
user3 | pass3 | workgroup
user4 | pass4 | workgroup

Samba accounts | passwords: exactly the same as Unix accounts above except there's no "group".

Samba workgroup: WORKGROUP
==============

==============
Windows Machine 1
Computer Name: Machine1
Workgroup: WORKGROUP
User Account: user1
Password: pass1
==============[INDENT]                 .
[/INDENT][INDENT]                 .
[/INDENT][INDENT]                 .
[/INDENT]==============
Windows Machine 4
Computer Name: Machine4
 Workgroup: WORKGROUP
 User Account: user4
 Password: pass4
 ==============

Here are the sharing (and related) settings of my smb.conf:

==============
[global]
workgroup = WORKGROUP
security = user
unix password sync = yes
map to guest = bad user

[homes]
comment = Home Directories
browseable = yes
read only = no
create mask = 0775
directory mask = 0775

[supershare]
comment = Shared According to User Permissions
path = /home/supershare
browseable = yes
read only = no
write list = user1, user2
create mask = 0775
directory mask = 0775

[public]
comment = Shared with All Authenticated Users
path =/home/public
browseable = yes
read only = no
write list = user1, user2
read list = @WORKGROUP
create mask = 0775
directory mask = 0775

==============

Currently, all windows machines can browse through "supershare",  "homes", "public" and their own personal folder, ex. user1 sees folder  named "user1", but does not see folder "user2".

All users can write to their own folders and to the "homes" folder *but*  files/folders created in the "homes" folder can only be seen by the  user who actually created them (therefore my belief of this whole thing  being a Unix user permission issue).

So far I have tried so many different approaches (in accordance to my  research) that I can't possibly remember them all, but the less common ones that I still remember are:

-- adduser.conf: changed DIR_MODE to 0775
-- double checked /etc/profile to make sure it was set to "umask 022"  (should it be 002?)
-- checked windows cmd >> net view for issues (there were none)

I believe it is clear what I want to achieve just by reading my  tentative smb.conf settings above but in any case, I want to share  folders with specific users, while allowing other users to read but not  write on certain folders while still being able to write to designated  folders.

So far, all I have accomplished is no sharing at all! Users can write to  certain folders on the server but only they can read/write on these  folders themselves. I hope this community can help me sort this out and that I  don't have to reinstall the the friendly but limited Windows Home  Server.

Thanks in advance!

---

### Post by LeoCortes on 2010-05-04
bump

---

### Post by jvin248 on 2010-05-04
Assuming you can see the share from other machines then from the command line on the server (or after using ssh into the server if it's headless) try:

$  sudo chmod 766 -R /path/to/directories/

 -R will recurse from target directory to any child directories in there.
 766 will make the directory and contained files into read/write but no execute for everyone accessing the directories.  Usually I expect new files placed there to be similarly corrected for read/write access.

The other option is to make all users belong to a group that has access to these and then use (for "group")

$   sudo chgrp group -R /path/to/directories/

I may have the order of 'group' and -R reversed (check with 'man chgrp')

---

### Post by jvin248 on 2010-05-04
This might also help

[http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic](http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic)

---

### Post by drdos2006 on 2010-05-04
Check this out. I found it really useful as a step by step tutorial to access the permissions, samba shares using Webmin to control the server.
//--------------------------------------------------------
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood
//-------------------------------------------------------

regards

---

