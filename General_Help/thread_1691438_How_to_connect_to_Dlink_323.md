---
title: "How to connect to Dlink 323"
date: 2011-02-19
forum: General Help
---

### Post by Iteria on 2011-02-19
I'm using 10.10 and I'm trying to mount my dlink 323. It mounts when I use this command:

```
sudo mount -t cifs //10.0.0.4/Volume_1 /media/NAS -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777
```

But then I add this to /etc/fstab it fails to mount on startup:
```
//10.0.0.4/Volume_1 /media/NAS -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777
```

I don't know what I did wrong.

Edit:
I figured out what the command should be:
```
//10.0.0.4/Volume_1 /media/NAS smbfs username=root,password=<password>,uid=1000,gid=120 0 0
```

---

### Post by Houchy on 2011-05-01
Hello,

I have the same problem, could anyone help please.

Thank you.
Houchy

---

### Post by 4ebees on 2011-09-21
And this was solved how exactly?


> **Iteria said:**
> I'm using 10.10 and I'm trying to mount my dlink 323. It mounts when I use this command:

```
sudo mount -t cifs //10.0.0.4/Volume_1 /media/NAS -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777
```

But then I add this to /etc/fstab it fails to mount on startup:
```
//10.0.0.4/Volume_1 /media/NAS -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777
```

I don't know what I did wrong.

Edit:
I figured out what the command should be:
```
//10.0.0.4/Volume_1 /media/NAS smbfs username=root,password=<password>,uid=1000,gid=120 0 0
```

---

### Post by Iteria on 2011-09-22
I can't really remember the specifics of how I came up with that. I'm sure it involved a lot of googling. The beginning might be different for you. the "//10.0.0.4/Volume_1" is simply the ip address and path of the NAS.

If you're still having trouble you should try installing gigolo. It'll mount everything for you automatically. The downside it is mounts it in the hidden folder ~/.gvfs which is worthless. Thus I created a shortcut to the mounted folder for ease of access.

hope this helps!

---

