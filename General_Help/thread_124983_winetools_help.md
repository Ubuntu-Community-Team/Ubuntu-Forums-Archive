---
title: "winetools help"
date: 2006-02-02
forum: General Help
---

### Post by psilo357 on 2006-02-02
i am trying to get winetools to work and something isnt working right.  Here is what i get right after install, what am i doing wrong?

randy@ubuntu:~$ cd Desktop
randy@ubuntu:~/Desktop$ dir
downloads  winetools-0.9jo-III
randy@ubuntu:~/Desktop$ cd winetools-0.9jo-III
randy@ubuntu:~/Desktop/winetools-0.9jo-III$ sudo ./install
Password:
Version: winetools-0.9
Release: 0.9
Installing WineTools to /usr/local/winetools...
ln: creating symbolic link `/usr/local/bin/wt' to `/usr/local/winetools/wt0.9jo': No such file or directory
ln: creating symbolic link `/usr/local/bin/winetools' to `/usr/local/winetools/wt0.9jo': No such file or directory
ln: creating symbolic link `/usr/local/bin/findwine' to `/usr/local/winetools/findwine': No such file or directory
Installing translations...
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt0.9.mo
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt0.9.moInstalled translations for fr to /usr/local/share/locale/fr/LC_MESSAGES/wt0.9.moInstalled translations for nb to /usr/local/share/locale/nb/LC_MESSAGES/wt0.9.moInstalled translations for pt_BR to /usr/local/share/locale/pt_BR/LC_MESSAGES/wt0.9.mo
Start WineTools as *normal* user with "wt". Don't use as root!
randy@ubuntu:~/Desktop/winetools-0.9jo-III$ cd -
/home/randy/Desktop
randy@ubuntu:~/Desktop$ wt
bash: wt: command not found
randy@ubuntu:~/Desktop$ winetools
bash: winetools: command not found
randy@ubuntu:~/Desktop$

why are the commands not available?

---

### Post by dcstar on 2006-02-02
[QUOTE=psilo357]i am trying to get winetools to work and something isnt working right.  Here is what i get right after install, what am i doing wrong?
.......
Installing WineTools to /usr/local/winetools...
[B]ln: creating symbolic link `/usr/local/bin/wt' to `/usr/local/winetools/wt0.9jo': No such file or directory
ln: creating symbolic link `/usr/local/bin/winetools' to `/usr/local/winetools/wt0.9jo': No such file or directory
ln: creating symbolic link `/usr/local/bin/findwine' to `/usr/local/winetools/findwine': No such file or directory[/B]
.......
randy@ubuntu:~/Desktop$ wt
bash: wt: command not found
randy@ubuntu:~/Desktop$ winetools
bash: winetools: command not found
randy@ubuntu:~/Desktop$

why are the commands not available?[/QUOTE]
Coz the links to them didn't work right.

Check /usr/local/winetools/ to see if there is anything in there, then run the highlighted commands  to make the links (with sudo)

---

### Post by psilo357 on 2006-02-02
ok, i try and make the links, and this is what i get, am i doing the command right?

randy@ubuntu:~$ sudo mkdir /usr/local/bin/wt
Password:
mkdir: cannot create directory `/usr/local/bin/wt': No such file or directory
randy@ubuntu:~$ sudo mkdir /usr/local/bin
randy@ubuntu:~$ sudo mkdir /usr/local/bin/wt
randy@ubuntu:~$ sudo ln /usr/local/bin/wt /usr/local/winetools/wt0.9jo
ln: `/usr/local/bin/wt': hard link not allowed for directory
randy@ubuntu:~$



thanks for the help again

peace

---

### Post by dcstar on 2006-02-02
[QUOTE=psilo357]ok, i try and make the links, and this is what i get, am i doing the command right?

randy@ubuntu:~$ sudo mkdir /usr/local/bin/wt
Password:
mkdir: cannot create directory `/usr/local/bin/wt': No such file or directory
randy@ubuntu:~$ sudo mkdir /usr/local/bin
randy@ubuntu:~$ sudo mkdir /usr/local/bin/wt
randy@ubuntu:~$ sudo ln /usr/local/bin/wt /usr/local/winetools/wt0.9jo
ln: `/usr/local/bin/wt': hard link not allowed for directory
randy@ubuntu:~$



thanks for the help again

peace[/QUOTE]
You shouldn't "mkdir" anything, those files should exist - if they don't then the install didn't work.

Delete them and run the install, or just forget winetools and use winecfg to set up your wine.

---

### Post by psilo357 on 2006-02-02
i can get wine installed using synaptics alright, and ran winecfg fine and all, but my problem is i cant get dvd decrypter to find my drives, any help would be appreciated

---

### Post by Sutekh on 2006-02-02
[QUOTE=psilo357]i can get wine installed using synaptics alright, and ran winecfg fine and all, but my problem is i cant get dvd decrypter to find my drives, any help would be appreciated[/QUOTE]
Forgive me if you've been asked this before, but have you setup the Windows compatability for DVDDecrypter to **Win NT 4.0** in winecfg?  This solved the problem for me.

---

### Post by psilo357 on 2006-02-02
in my winecfg, there is no data at all, it is just a blank page, I did enter the what it said on the guide, but to no avail, i still cant get it to work

thanks

---

### Post by Sutekh on 2006-02-02
Did you *run* winecfg?  Or did you look inside some file? 

At a terminal windows type **winecfg**

Or press Alt+F2 and then type **winecfg** and run it.

---

