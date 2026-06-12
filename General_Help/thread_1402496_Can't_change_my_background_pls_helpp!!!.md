---
title: "Can't change my background pls helpp!!!"
date: 2010-02-09
forum: General Help
---

### Post by Crys1sw0w on 2010-02-09
Ok ill be quick. When i go from my start menu prefrences, change background wallpaper, i get the message that the application for changing the background cant write somewhere and that is banned by my administrator or supervisor..... i think the path was /desktop/gnome/background/picture_options. I tryed to find it but immpossible... pls help... i got the same picture all the time :(((((
 
P.S forgot to mention that i use 7.04 edubuntu

---

### Post by hansdown on 2010-02-09
Welcome to the forum Crys1sw0w.

7.04 is not receiving any updates now, as it is outdated.

Try right-clicking your desktop> change desktop picture.

Have you considered a newer version of ubuntu?

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by jessel on 2010-02-09
> i get the message that the application for changing the background cant write somewhere and that is banned by my administrator or supervisorI'm guessing that the filesystem is full and you have no disk space left. The reason I'm guessing this is because even if you do not have administrative priviledges I'd think you could change the background. If this is the case you will be having problems with any applications that need to write temporary files (like when printing).

Anyway, the easiest way to check, that I can think of is using gparted. Gparted requires administrative access, and I don't know if it is a default application. Gparted would show up on the startup menu under system... You would then be looking at a gui showing all your disks how they are mounted and how much space is available. There is also a command called "df". to get information on using this command:
```
man df
```Another scenario could be that the /tmp directory does not allow users write access. I can't think of any reason why this would suddenly happen.
```
ls -al /tmp
```The permission bit for . (the top line) should look like drwxrwxrwx, and not drwx------

---

