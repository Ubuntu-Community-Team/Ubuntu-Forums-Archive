---
title: "Need help with write access on raid5 mount and network access"
date: 2010-04-22
forum: General Help
---

### Post by snkmad on 2010-04-22
I'm running ubuntu 9.10, and created a softraid5 with no problems.
Now i need it to automount with user read/write access, and i need to make some network share folders.

My fstab has the following line for the raid:
```
/dev/md0        /media/raid  auto    rw,user,auto,exec 0       0
```

After i mounted it, i changed the permission with:
```
sudo chmod 777 /media/raid/
```
So now i can create folders and files on it.
Then i created some shares, one with guest access and other with no guest access.

Now the questions:
1) If i access the guest shared folder via WinXP, i create files and folders, but they appear locked on ubuntu, so i cant access them until i change the permissions. If i go to proprieties/Permissions, the owner is "nobody". 
2) What password do i need to use on WinXP, and i try to access the non-guest shared folded? Do i need to create a user just for that?

---

### Post by skulls on 2010-04-30
Hi,

In my experience, it was more difficult and painful to properly create a softraid than it was to share folders within a windows network... :P

Regarding question 1, I think it's partly related to the fact that the folder you are sharing is not formatted with NTFS and is probably ext3 or ext4. (did I guess?)
I am saying this because I have the same problem as you, files created by windows user appear as locked in ubuntu (I use Linux Mint 8 at the moment, but it should apply as well). I was just looking for a solution and I came upon your question... 

I think the following solution should solve your problem (and mine as well ;-) , although I haven't had time to test it, I will do it later today)

> oceanmaster says

Wanting to share a folder and having problems? Try this:

1.
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.orig
(backs up the smb.comf samba file)

2.
gksu gedit /etc/samba/smb.conf
(opens the smb.conf file)

3.
Add this line below the “usershare allow guests = yes” line and save it
usershare owner only = False

4. (might not have to do this step)
sudo /etc/init.d/samba restart
(restart samba service)

from: [http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/")

Let me know if this works?

---

