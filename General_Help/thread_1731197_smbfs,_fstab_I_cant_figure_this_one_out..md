---
title: "smbfs, fstab I cant figure this one out."
date: 2011-04-16
forum: General Help
---

### Post by jquis8411 on 2011-04-16
I am trying to mount a smb share on an ubuntu machine and for the life of me I can't figure out the fstab entry. The server is running fine and the windows machines can map their shares fine, I just cant figure out the fstab entry for an ubuntu box.at this point the fstab looks like this(although I have tried many variations)```
 //server/path/share /path/mount/point smbfs credentials=/root/.credentials, uid=1000, gid=1000 0 0
```
 smbfs is installed on the client, the server is in the hosts file, the uid and gid are both correct. If it matters the file  I am trying to connect to is not browseable and is read only=no. It is also on a vfat partition but if I understand correctly the smbfs supersedes this fact. The only clue I have is that when I run sudio mount -a it says that this line is bad. I hope someone has some clues, I feel like I googled this to death but I am a terrible googler. Thanks in advance.

---

### Post by seawolf167 on 2011-04-16
Try this line (this is what I use to add Windows share fstab network entries)

```
//network/share/location /mount/point cifs exec,credentials=/etc/cifspw 0 0
```

where /etc/cifspw is a plain text file that contains the login username & password

i.e.

```
username=[I]username
[/I]password=*password*
```

then chmod 600 that file so only root can read/write it

---

### Post by jquis8411 on 2011-04-16
You got it!!! Your line worked but more importantly when I plugged in my values it first returned an error that said it couldn't find the file I was trying to mount, I had the name of the actual file instead of the name of the samba share. Big error on par and many thanks to you.

---

### Post by seawolf167 on 2011-04-16
Awesome, I love easy fixes :)

---

