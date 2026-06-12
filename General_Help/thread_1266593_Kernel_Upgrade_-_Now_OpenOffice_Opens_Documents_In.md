---
title: "Kernel Upgrade - Now OpenOffice Opens Documents In Read Only"
date: 2009-09-14
forum: General Help
---

### Post by Andysan on 2009-09-14
Hi,

I have upgraded from kernel 2.6.30 to 2.6.31 today to fix the sound skipping issue that many have experienced.  It was my first kernel compile following [this]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2") tutorial.  I used the config from my current kernel and left everything else untouched.

All seems to have gone OK, however when accessing mounted shares OpenOffice Writer opens documents in Read-Only mode.  I can create and delete files so permissions are fine and local documents open fine.  I can confirm when booting into 2.6.30 the same document from the same location opens correctly (i.e. not in read only mode).  Shares are mounted in fstab as follows:
```

//ipaddress/directory /mnt/directory/directory cifs username=user,password=pass,users,noperm,auto 0 0
```

Can anyone suggest what I may have done please as it would seem that Google is not my friend today - using Ubuntu Jaunty?  Thanks.

---

### Post by Mr_Bumpy on 2009-10-30
I can confirm this problem on two systems since upgrading to Karmic (one Ubuntu and one Xubuntu).  I can edit the files fine if I browse to the share using nautilus (smb://).  I hope someone knows a fix/workaround for this problem.

---

### Post by Mr_Bumpy on 2009-10-30
Okay, so I have solved the problem on my end.  I was previously mounting my share with the following command:
```
sudo mount -t cifs //axeserver/axedata /media/AXEData -o credentials=/home/bumpy/.auth.racserver.bumpy,noperm,nounix
```
When opening files in OpenOffice, they would open as read-only.  However, everything works now that I have changed my mount command to:
```
sudo mount -t cifs //axeserver/axedata /media/AXEData -o credentials=/home/bumpy/.auth.racserver.bumpy,uid=bumpy,gid=bumpy
```
So, it would seem that specifying the user and group id makes a difference for OpenOffice.  Also of note: mounting shares using SMB4K works as well.

Hope this helps!

---

