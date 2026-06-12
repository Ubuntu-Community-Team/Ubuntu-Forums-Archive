---
title: "mount windows share"
date: 2009-10-10
forum: General Help
---

### Post by Switch08 on 2009-10-10
I've have googled around for a while only to still have no idea on how to mount a windows share.

sudo mount -t smbfs -o username=Switch08,password="mypass" //IP#/Switch08 /mnt/target
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

sudo mount -t cifs //IP#/Switch08 /mnt/target
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I've tried several other methods all with the same error.

any ideas how to resolve this issue?

thankyou

---

### Post by ZaHACKieL on 2009-10-10
> **Switch08 said:**
> I've have googled around for a while only to still have no idea on how to mount a windows share.


You mean....you have like a NTFS partition and you want to mount it on Ubuntu? is that the problem?

---

### Post by akakingess on 2009-10-10
You should just be able to go to the 'Places' menu and see it listed there, select it and it will open it and should also mount it onto the desktop at the same  time.  To have it automount you need to edit (I believe) fstab.

---

### Post by abhilashm86 on 2009-10-10
you can automount ntfs drives in ubuntu, so every time you boot-up, it'll mount itself.....
check this thread for [installing and details about mounting....]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by DeMus on 2009-10-10
Simply do this:

[COLOR="Red"]_**Auto mount Windows disks**_[/COLOR]
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok, so when that returns you to user@pcname, that should be installed                 

Next, make sure you have **_[COLOR="Red"]NO[/COLOR]_** drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.

Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by akakingess on 2009-10-10
Dang, I learn at least 10 new things a night when I read this forum, thanks for the extra information/lesson DeMus!!!

---

### Post by Switch08 on 2009-10-10
I have searched for mount error(13): Permission denied
Refer to the mount.cifs(:cool: manual page (e.g. man mount.cifs) and haven't found the solution just yet.

So far each method giving ends up with the same error message.

I'm trying to connect to a share folder on my winxp at my parents house that is set up to share a folder with read and write privileges that is password protected. I hate windows so I decided  to start using Linux. I have Ubuntu 9.10 and have no problem mounting attached drives.

I don't have a problem mounting shares on my local network since Ubuntu makes it very easy to do.

But in this case it appears that I have to use a command like 

sudo mount -t smbfs -o username=Switch08,password="mypass" //IP# of  parents house/Switch08 /mnt/target

which gives me the error message

mount error(13): Permission denied
Refer to the mount.cifs(:cool: manual page (e.g. man mount.cifs)

any help will be appreciated

thank you

---

### Post by Switch08 on 2009-10-11
#!/bin/bash
echo ENTER THE IP ADDRESS TO CONNECT TO
read IP
echo ENTER THE SHARE NAME
read NAME
sudo mount.cifs //$IP/$NAME /mnt/target -o username=guest
echo Press enter to quit 
read enter

OK I figured out the right format and wrote a BASH

maybe I'll include opening /mnt/target in it instead of a location launcher to file:///mnt/target

---

