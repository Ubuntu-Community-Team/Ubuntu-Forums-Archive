---
title: "FTP setup questions"
date: 2006-01-23
forum: General Help
---

### Post by lungdart on 2006-01-23
I'm using proftpd and webmin-proftpd for my ftp server. Have a user "ftpuser" in "ftpgroup" with a home folder of /home/ftp I'm directories on the server using

```
sudo mount --bind "directory" "directory in /home/ftp"
```

Is there any way to do all that on start up with fstab maybe? All my shit is on /dev/hdd1 which is mounted to /pub which is also set up for smb shares on my network. So mount --bind seemed like the best option for me. Is there a better way or a way to auto mount binds?

Another question. when someone connected to my ftpserver and uploads, its restricted to ftpuser, and i dont have full access. I find my self sudo'ing everything to rename move re orginize, etc. I want it so its restricted to ftpgroup and also put my login user under that group as well, so i have full access to it. Anyway to do this? In the set up users and groups in the system menu, theres only a "main group" option, can i even add me to other groups? chmoding doesnt seem like a good idea because then it will apply to everyone else outside ftpuser aswell and not just me.

Any help? thanks in advance.

---

### Post by lungdart on 2006-01-25
Bump, figured out how to mount binds, but i still dont have access to the ftp files from ftpuser in /home/ftp. Is there at all anyway to make my user have access to ftpusers files as well? some sort of double ownership? or parent child users?

---

