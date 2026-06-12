---
title: "about mouting for different users"
date: 2009-07-02
forum: General Help
---

### Post by kfc123 on 2009-07-02
Hi there,
I am sharing some folders from windows to linux. In windows side, I have setup several user accounts and in linux corresponding accounts with same name as those in windows are setup. For user A in windows, I am going to share a folder A such that when user A in linux log in it will mount folder A into automatically; when user B logon, it mount folder B instead. I wonder how to implement this ?

---

### Post by bazmonkey on 2009-07-02
Are these two separate partitions we're talking about?  Or are you wanting to allow user A to only access directory A on your windows partition, and the same for user B?  You can't exactly mount specific folders.

1) Windows' and Ubuntu's file permissions and access control aren't the same, and don't work together.  The usernames may match for convenience, but that doesn't "link" them or anything like that.

2) Neither FAT32 or NTFS support UNIX permissions, so the only way you can control access is by the partition as a whole.  IOW, you can only control what user A can do with the partition as a whole, not what the user can do with specific directories in the partition.  Think of the windows partition as, oh, a USB flash drive.  If you can mount it, you can see it.

3) AFAIK, it would take multiple partitions for each user's folder to do what you want to do how you want to do it.

---

### Post by Jebtrix on 2009-07-02
Open Terminal:
sudo apt-get install smbfs


Open gedit and create new text file:

```
#!/bin/sh

sharetarget=/media/sharename/
if [ -d $sharetarget ]; then
	sudo mount -t smbfs //windowsbox/sharename/ $sharetarget -o username=masta,password=masta
fi
```

Name it ".gdmlogin", save it in the root of your user directory ie /home/user/

In Terminal:
```
chmod +sx ~/.gdmlogin
```

Goto System > Preferences > Startup Applications > Add
Add the /home/user/.gdmlogin as the command, call name & comment whatever you like.

That is will get things mounting on login.

Now for unmounting on logoff:

Open gedit and create new text file:
```

#!/bin/sh

umount /media/sharename
```

Name it ".gdmlogout", save it in the root of your user directory 


In Terminal:
chmod +x ~/.gdmlogout
gksudo gedit /etc/gdm/PostSession/Default

Paste this right before "exit 0":

```
logoutscript="$HOME/.gdmlogout";
if [ -x "$logoutscript" ] ; then
  sudo "$logoutscript"
fi
```

Save file.

Logoff and back in to see fruits of your labor =D>

---

### Post by Jebtrix on 2009-07-02
Almost forgot, you need to do that for each user on the linux box, except point to different windows shares of course.

---

