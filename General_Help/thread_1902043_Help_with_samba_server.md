---
title: "Help with samba server"
date: 2011-12-29
forum: General Help
---

### Post by jgv115 on 2011-12-29
Hello community,

First of all I am a linux noob, however I am quite computer literate.

I wanted to create a samba server on Ubuntu 11.10. I followed the documentation on the Ubuntu website and this is what I've done:

I've set workgroup = WORKGROUP
I set security = user

I made a directory in mnt called "backup" so the path is /mnt/backup

Then I created a little section at the bottom like so:

```
[backup]
   comment = Backup
   path = /mnt/backup
   browsable = yes
   guest ok = yes
   read only = no
   writeable = yes
   directory mask = 0777
   create mask = 0777
```With this setup, I can see the computer "UBUNTU" on windows explorer (on Windows 7) and I can see a share called "backup". I can write files into this folder with Windows however, if I create a directory inside "backup", I can't write to it anymore. Is there a way to make the whole of "backup" 777?

I don't really mind about security atm because I'm in a very small home network. But shouldn't this setup allow all clients to read/write/execute? How come I can't write to my shared folder?

Thanks in advance!

---

### Post by jgv115 on 2011-12-29
bump

---

