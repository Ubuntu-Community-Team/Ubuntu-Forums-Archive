---
title: "Help - Password Prompt on Bootup"
date: 2006-02-26
forum: General Help
---

### Post by Hawk2k2 on 2006-02-26
Everytime i reboot the PC i get a password prompt.

First it pauses on this screen:
[IMG]http://www.hawk2k2.ath.cx/ubuntu/1.jpg[/IMG]

Then goes to this screen where i havto type the password:
[IMG]http://www.hawk2k2.ath.cx/ubuntu/2.JPG[/IMG]

I have done many configurations at once so i dont hav a clue which one caused this :(. It is really annoying cause this box is sitting in the closet with network cable and power, so i havto plug a keyboard in everytime it gets rebooted.

Any ideas?

Thanks in advance
Hawk

---

### Post by ranf on 2006-02-26
Looks like it is mounting remote file systems. Something like NFS or SMB.
Show your /etc/fstab please.

---

### Post by Hawk2k2 on 2006-02-26
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro,usrquota,grpquota,noatime,data=writeback 0       1
/dev/hda1       /boot           ext3    defaults,usrquota,grpquota       0       2
/dev/hda2       none            swap    sw              0       0
//win2003-server/c  /home/admin/network/server/c  smbfs  workgroup=home_lan,password=****,uid=1000,ip=192.168.0.4,gid=1000,username=Administrator  0  0
\\win2003-server\d  /home/admin/network/server/d  smbfs  workgroup=home_lan,password=****,uid=1000,ip=192.168.0.4,gid=1000,username=Administrator  0  0
\\win2003-server\e  /home/admin/network/server/e  smbfs  workgroup=home_lan,password=****,uid=1000,ip=192.168.0.4,gid=1000,username=Administrator  0  0
\\win2003-server\f  /home/admin/network/server/f  smbfs  workgroup=home_lan,password=****,uid=1000,ip=192.168.0.4,gid=1000,username=Administrator  0  0
\\builtforpower\downloads  /home/admin/network/desktop/g  smbfs  workgroup=home_lan,uid=1000,ip=192.168.0.2,gid=1000,username=Guest  0  0

```

i used webmin to mount the shares into that folder :???:
as u can see i hav also used the faster file system mod. i reverted bak to defaults thinking that was the reason, but still the same thing.

Hawk

---

### Post by Stormbringer on 2006-02-26
Using backslashes in fstab for your windows-shares is dead wrong ... here are the lines in question:

\\win2003-server\d
\\win2003-server\e
\\win2003-server\f
\\builtforpower\downloads

Correct them to slashes ("/") - and try again ... should work fine afterwards.

EDIT: Should read...

//win2003-server/d
//win2003-server/e
//win2003-server/f
//builtforpower/downloads

---

