---
title: "Mounting a samba share as user / via boot-up(fstab) doesn't work"
date: 2006-03-18
forum: General Help
---

### Post by justBE on 2006-03-18
Hello there,

I used the guide available at ubuntuguide.org to mount my terastation's samba-shares on bootup, but it doesn't work. When I try mounting them by hand as my default user I get the following:

joerg@cheese:~$ mount /media/TV/
mount: only root can mount //192.168.0.150/TV on /media/TV


My /etc/fstab looks like this:
> 
//192.168.0.150/TV    /media/TV  smbfs   credentials=/home/joerg/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.0.150/Movies    /media/Movies  smbfs   credentials=/home/joerg/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.0.150/Mp3s    /media/Mp3s  smbfs   credentials=/home/joerg/.smbcredentials,dmask=777,fmask=777   0       0
 
doing a ls -al on /media shows these settings:
> 
drwxrwxrwx 29 root root  4096 2006-01-30 21:51 .
drwxr-xr-x 22 root root  4096 2006-03-18 16:54 ..
lrwxrwxrwx  1 root root     6 2006-01-20 16:15 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2006-01-20 16:15 cdrom0
drwxr-xr-x  2 root root  4096 2006-01-20 16:15 cdrom1
lrwxrwxrwx  1 root root     7 2006-01-20 16:15 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2006-01-20 16:15 floppy0
drwxrwxrwx  2 root root  4096 2006-01-30 21:51 Movies
drwxrwxrwx  2 root root  4096 2006-01-30 21:51 Mp3s
dr-xr-xr-x  1 root root  4096 2006-03-15 18:55 sda1
dr-xr-xr-x  1 root root 49152 2006-03-18 15:28 sdb1
drwxrwxrwx  2 root root  4096 2006-01-30 21:51 TV
 
/home/joerg/.smbcredentials looks like this:
> 
username=myusername
password=mypassword
 
and has the following permissions etc:
-rwxrwxrwx 1 joerg joerg 34 2006-02-19 14:54 /home/joerg/.smbcredentials


Now when I do a sudo mount /media/Mp3s for example - it works.. so as superuser you're allowed to mount etc, just not as plain user.. and it doesn't do it during bootup. 

Did I miss something or what might be wrong? I am a tad puzzled :\


Any ideas / suggestions?


Thanks and best regards,
-J

---

### Post by magisterludi on 2006-03-18
Put "user" in the options 

like that:
```

//192.168.0.150/TV /media/TV smbfs credentials=/home/joerg/.smbcredentials,dmask=777,fmask=777,user 0 0

```

you may put there "users" instead of "user" if not only the user who
mounted it should be able to unmount.

Plz read ```
man mount
``` and ```
man fstab
```

---

### Post by justBE on 2006-03-20
thanks :)
 
mounting as user works now, however mounting on startup does -not- :\
 
What permissions do I have to have on the credentials file and or mount point directories in order to mount the directories during bootup?
 
 
cheers,
-j

---

### Post by mr.p on 2006-03-20
[QUOTE=justBE]thanks :)
 
mounting as user works now, however mounting on startup does -not- :\
 
What permissions do I have to have on the credentials file and or mount point directories in order to mount the directories during bootup?
 
 
cheers,
-j[/QUOTE]
Under options put "auto", that should do it.

---

