---
title: "Installing Adobe Flash Player on Ubuntu Server"
date: 2009-12-19
forum: General Help
---

### Post by jon80 on 2009-12-19
I'm trying to install Adobe Flash Player (download link [http://www.adobe.com/products/flashplayer/productinfo/instructions](http://www.adobe.com/products/flashplayer/productinfo/instructions)), however, I tried:

1. Running the .deb file but when I opening it with KPackage a non-descriptive error is displayed.
2. Running the .deb file from the Terminal:
administrator@elsueno:~/Desktop$ chmod 755 install_flash_player_10_linux.deb
administrator@elsueno:~/Desktop$ ls -latr
total 3956
-rw-r--r--  1 administrator administrator    5453 2009-12-10 06:11 trash.desktop
-rw-r--r--  1 administrator administrator     156 2009-12-10 06:11 Home.desktop
-rw-r--r--  1 administrator administrator     113 2009-12-10 06:11 .directory
drwxr-xr-x 25 administrator administrator    4096 2009-12-19 12:06 ..
-rwxr-xr-x  1 administrator administrator 4022162 2009-12-19 12:21 install_flash_player_10_linux.deb
drwxr-xr-x  2 administrator administrator    4096 2009-12-19 12:21 .
administrator@elsueno:~/Desktop$ ./install_flash_player_10.linux.deb
bash: ./install_flash_player_10.linux.deb: No such file or directory
administrator@elsueno:~/Desktop$
3. Running apt from the Terminal:
administrator@elsueno:~$ sudo apt-get flashplugin-nonfree
[sudo] password for administrator:
E: Invalid operation flashplugin-nonfree

4. Running dpkg from the terminal, however it seems that AMD64 architecture is not supported by Adobe Flash Player 10.

administrator@elsueno:~/Desktop$ ls -latr
total 3956
-rw-r--r--  1 administrator administrator    5453 2009-12-10 06:11 trash.desktop
-rw-r--r--  1 administrator administrator     156 2009-12-10 06:11 Home.desktop
-rw-r--r--  1 administrator administrator     113 2009-12-10 06:11 .directory
drwxr-xr-x 25 administrator administrator    4096 2009-12-19 12:06 ..
-rwxr-xr-x  1 administrator administrator 4022162 2009-12-19 12:21 install_flash_player_10_linux.deb
drwxr-xr-x  2 administrator administrator    4096 2009-12-19 12:21 .
administrator@elsueno:~/Desktop$ dpkg -install install_flash_player_10_linux.deb
dpkg: unknown option -n

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
administrator@elsueno:~/Desktop$ dpkg -i install_flash_player_10_linux.deb
dpkg: requested operation requires superuser privilege
administrator@elsueno:~/Desktop$ sudo dpkg -i install_flash_player_10_linux.deb
dpkg: error processing install_flash_player_10_linux.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 install_flash_player_10_linux.deb
administrator@elsueno:~/Desktop$

Workaround anyone?

:confused:


Related links
------------------
Installation instructions at:
[http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-3](http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-3)

System requirements at: [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

---

### Post by oldos2er on 2009-12-19
Your commands are incorrect. Instead of "administrator@elsueno:~/Desktop$ ./install_flash_player_10.linux.deb", run **sudo dpkg -i install_flash_player_10.linux.deb**

---

