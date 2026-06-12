---
title: "winetools problems"
date: 2006-02-24
forum: General Help
---

### Post by ubuntulover1 on 2006-02-24
i cant install winetools it gives these errors what should i do? :confused:  thanx.

```

Version: winetools-0.9
Release: 0.9
Installing WineTools to /usr/local/winetools...
ln: creating symbolic link `/usr/local/bin/wt' to `/usr/local/winetools/wt0.9jo': No such file or directory
ln: creating symbolic link `/usr/local/bin/winetools' to `/usr/local/winetools/wt0.9jo': No such file or directory
ln: creating symbolic link `/usr/local/bin/findwine' to `/usr/local/winetools/findwine': No such file or directory
Installing translations...
Start WineTools as *normal* user with "wt". Don't use as root!
sasa@ubuntu:~/Desktop/winetools-0.9jo-III$ cd -
/home/sasa/Desktop
sasa@ubuntu:~/Desktop$ wt
bash: wt: command not found
sasa@ubuntu:~/Desktop$ winetools
bash: winetools: command not found

```

---

### Post by ubuntulover1 on 2006-02-24
```
sasa@ubuntu:~$ sudo mkdir /usr/local/bin/wt
Password:
mkdir: cannot create directory `/usr/local/bin/wt': No such file or directory
sasa@ubuntu:~$ sudo mkdir /usr/local/bin
sasa@ubuntu:~$ sudo mkdir /usr/local/bin/wt
sasa@ubuntu:~$ sudo ln /usr/local/bin/wt /usr/local/winetools/wt0.9jo
ln: `/usr/local/bin/wt': hard link not allowed for directory
sasa@ubuntu:~$
```

please help me :confused:

---

### Post by MightyFlea on 2006-02-28
Hey there,

have you started the installation as root?

(You should install winetools as root, but then use it as a normal user to set up your wine.)

I did get this output, just now:

```

michael@elyn:~/Source/winetools-0.9jo-III$ sudo ./install
Password:
Version: winetools-0.9
Release: 0.9
Installing WineTools to /usr/local/winetools...
Installing translations...
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt0.9.mo
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt0.9.mo
Installed translations for fr to /usr/local/share/locale/fr/LC_MESSAGES/wt0.9.mo
Installed translations for nb to /usr/local/share/locale/nb/LC_MESSAGES/wt0.9.mo
Installed translations for pt_BR to /usr/local/share/locale/pt_BR/LC_MESSAGES/wt0.9.mo
Start WineTools as *normal* user with "wt". Don't use as root!
michael@elyn:~/Source/winetools-0.9jo-III$ cd
michael@elyn:~$ wt
no suitable Wine directory found...
Wine 0.9.8
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.8".
Calls to wine are executed as  "wine".
(... and so on)

```

I use Kubuntu 5.10, by the way, with KDE 3.5.1; and wine 0.9.8 from the sourceforge repository. (Not that that should make a difference here.)

---

