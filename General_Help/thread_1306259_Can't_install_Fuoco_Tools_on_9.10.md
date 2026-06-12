---
title: "Can't install Fuoco Tools on 9.10"
date: 2009-10-30
forum: General Help
---

### Post by chmacka on 2009-10-30
I couldn't start Fuoco after upgrading Ubuntu from 9.04 to 9.10, so I uninstalled it (with uninstall.sh), but I now can't install it:

```
chmacka@chmacka-desktop:/media/External/chmacka/Downloads/Fuoco Tools/FuocoToolsFull0.0.7e$ sudo ./install.sh
you have the power lol
installing...
remove icons
remove scripts
rm: cannot remove `/usr/bin/FuocoConfiguration.kmdr': No such file or directory
remove Menu link
copying old config file in /tmp. !!IF YOU REBOOT OLD CONFIG FILES WILL BE DELETED!!
cp: cannot stat `/home/chmacka/.fuoco/treestore.txt': No such file or directory
remove old config files
.
..
installing new version...
Converter only stable : 1.0.0b 
..
...
creating /usr/share/fuoco  ...
copy config files  ...
if exist i will replace only files
if exist i will replace only files
done
license file
done
copy script  ...
done
copy .dekstop files  ...
done
copy icons  ...
done
set chmod for interfaces 
chmod: cannot access `/usr/share/454.0.Chapter_Sel_01.png': No such file or directory
chmod: cannot access `/usr/share/Defaultfunctions.txt': No such file or directory
chmod: cannot access `/usr/share/Documentation.txt': No such file or directory
chmod: cannot access `/usr/share/finished.ogg': No such file or directory
chmod: cannot access `/usr/share/Fuctionloaded.txt': No such file or directory
chmod: cannot access `/usr/share/Main_Menu_01.png': No such file or directory
chmod: cannot access `/usr/share/treestorenew.txt': No such file or directory
done
checking for kommander
.
..
...
WARMING WARMING kommander is not installed!! check if you can execute,on your terminal , kommander with this :
kmdr-executor
if a windows appears with this error:Error: no dialog given. Use --stdin option to read dialog from standard input. 
kommander is installed IF NOT you must write this on a terminal,you must be on internet..,FOR UBUNTU USE THIS :  
sudo apt-get install kommander


```But "kommander" is installed:

```
chmacka@chmacka-desktop:/media/External/chmacka/Downloads/Fuoco Tools/FuocoToolsFull0.0.7e$ sudo apt-get install kommander
Reading package lists... Done
Building dependency tree        
Reading state information... Done
kommander is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by theLured on 2009-11-17
I had the same problem. Running this worked for me
sudo apt-get install kommander-kde3
whereis kmdr-executor

---

### Post by chmacka on 2009-11-17
Thanks!

---

