---
title: "Where is application after install?"
date: 2010-02-18
forum: General Help
---

### Post by Silvernail on 2010-02-18
Some of the things that happen, I just not understand why.

Goto synaptic and search 'disk editor'. Get about half page. Select 2: 'ide', 'ncurses-hexedit'.

Mark and install.

> dave@dave:~$ man  ncurses-hexedit
No manual entry for ncurses-hexedit
dave@dave:~$ man ncurses-hexedit
No manual entry for ncurses-hexedit
> 
dave@dave:~$ sudo apt-get install ncurses-hexedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ncurses-hexedit is already the newest version.
The following packages were automatically installed and are no longer required:
  wavpack dia-libs unixodbc libopal3.6.4 odbcinst1debian1 flac libpt2.6.4-plugins libpt2.6.4 dia-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
> 
dave@dave:~$ ncurses-hexedit
ncurses-hexedit: command not found
> 
dave@dave:~$ which ncurses-hexedit
> 
dave@dave:~$ whereis ncurses-hexedit
ncurses-hexedit:> 
dave@dave:~$  which ide> 
dave@dave:~$ whereis ide
ide:
dave@dave:~$ 
> dave@dave:~$ locate ncurses-hexedit | grep bin
dave@dave:~$ locate ncurses-hexedit | grep sbin> 
dave@dave:~$ locate ncurses-hexedit
/usr/share/doc/ncurses-hexedit
/usr/share/doc/ncurses-hexedit/AUTHORS
/usr/share/doc/ncurses-hexedit/NEWS.gz
/usr/share/doc/ncurses-hexedit/README.Debian
/usr/share/doc/ncurses-hexedit/README.gz
/usr/share/doc/ncurses-hexedit/changelog.Debian.gz
/usr/share/doc/ncurses-hexedit/changelog.gz
/usr/share/doc/ncurses-hexedit/copyright
/usr/share/doc/ncurses-hexedit/hexedit.lsm
/usr/share/doc/ncurses-hexedit/hexeditor.texinfo.gz
/var/cache/apt/archives/ncurses-hexedit_0.9.7-14ubuntu1_i386.deb
/var/lib/dpkg/info/ncurses-hexedit.list
/var/lib/dpkg/info/ncurses-hexedit.md5sums
/var/lib/dpkg/info/ncurses-hexedit.postinst
/var/lib/dpkg/info/ncurses-hexedit.prerm
dave@dave:~$ 


> dave@dave:~$ sudo aptitude install  /var/cache/apt/archives/ncurses-hexedit_0.9.7-14ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "/var/cache/apt/archives"
Couldn't find any package whose name or description matched "/var/cache/apt/archives"
The following packages will be REMOVED:
  dia-common{u} dia-libs{u} flac{u} libopal3.6.4{u} libpt2.6.4{u} libpt2.6.4-plugins{u} odbcinst1debian1{u} unixodbc{u} wavpack{u} 
0 packages upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 43.7MB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 208874 files and directories currently installed.)
Removing dia-common ...
Removing dia-libs ...
Removing flac ...
Removing libopal3.6.4 ...
Removing libpt2.6.4-plugins ...
Removing libpt2.6.4 ...
Removing unixodbc ...
Removing odbcinst1debian1 ...
Removing wavpack ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

dave@dave:~$ sudo ncurses-hexedit
sudo: ncurses-hexedit: command not found
dave@dave:~$ 


I'm going to stop here. I need help.

Thanks for putting up with this old man.
Thanks
Dave

---

### Post by jruberto on 2010-02-18
i believe the executable is called hexedit (hexeditor?) and it should be in /usr/bin

---

### Post by wrose51106 on 2010-02-18
Try hexedit

-Bill

---

### Post by Silvernail on 2010-02-19
> dave@dave:~$ hexedit
The program 'hexedit' is currently not installed.  You can install it by typing:
sudo apt-get install hexedit
hexedit: command not found
dave@dave:~$ 

What did I install???????

What about 'ide'?

I used 'ncurses-hexedit' as an example because any searches for 'ide' gave me hits on 'video', 'side', and a  hundred other words.

---

### Post by jruberto on 2010-02-19
the result of installing the ncurses-hexedit package is /usr/bin/hexeditor

```
jruberto@river:~$ which hexeditor
jruberto@river:~$ sudo apt-get install ncurses-hexedit
Reading package lists... Done
....snip.....
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
jruberto@river:~$ which hexeditor
/usr/bin/hexeditor

```

---

