---
title: "LInux DC ++ slow me down"
date: 2006-05-31
forum: General Help
---

### Post by BeNi.G on 2006-05-31
I try to connect to a hub in Linux dc++ (that I download from syntapic) and when I connected to a one hub my CPU processor get crazy into 100%
can I fix that??

I have 384 MB of RAM

TNX

---

### Post by nemtudod on 2006-05-31
try to cvs

[http://linuxdcpp.berlios.de/document.php?id=1](http://linuxdcpp.berlios.de/document.php?id=1)

---

### Post by BeNi.G on 2006-05-31
I cant understand how to download from the CVS...
I new in linux...

---

### Post by Sheinar on 2006-05-31
[QUOTE=BeNi.G]I cant understand how to download from the CVS...
I new in linux...[/QUOTE]
Open up a terminal

c/p: 
```
cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
```
Press enter when it asks for a password

c/p: 
```
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp
```

---

### Post by BeNi.G on 2006-05-31
look
> beni@Miranda:~$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
bash: cvs: command not found
beni@Miranda:~$


---

### Post by Sheinar on 2006-05-31
sudo apt-get install cvs scons

---

### Post by BeNi.G on 2006-05-31
ok thanks, now I in the compling level
I can compling I do what the the readme file tell me
and the scons tell me that I need G++ , where can I get that?

---

### Post by Sheinar on 2006-05-31
sudo apt-get install build-essential should install g++ and the other basic things you need.

---

### Post by BeNi.G on 2006-05-31
now this problam apear
> beni@Miranda:~$ cd /home/beni/linuxdcpp
beni@Miranda:~/linuxdcpp$ scons
scons: Reading SConscript files ...
Checking for g++ >= 3.4...ok
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.6... failed
gtk+ >= 2.6 not found.


---

### Post by Sheinar on 2006-05-31
Try sudo apt-get install libgtk2.0-dev

---

### Post by nemtudod on 2006-05-31
sudo apt-get install libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1 libglademm-2.4-1 scons

run scons

[http://ubuntuforums.org/showthread.php?t=28378&highlight=linuxdcpp](http://ubuntuforums.org/showthread.php?t=28378&highlight=linuxdcpp)

---

### Post by BeNi.G on 2006-05-31
I tryed that

> beni@Miranda:~$ sudo apt-get install libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-dev g++-3.4 libgtk libgtk2.0-bin libgtk2.0-common g++ libgtkmm libglademm scons
Reading package lists... Done
Building dependency tree... Done
libgtk2.0-dev is already the newest version.
zlib1g-dev is already the newest version.
E: Couldn't find package libgtk
beni@Miranda:~$ sudo apt-get install libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1 libglademm-2.4-1 scons
Reading package lists... Done
Building dependency tree... Done
libgtk2.0-dev is already the newest version.
zlib1g-dev is already the newest version.
libgtk2.0-0 is already the newest version.
libgtk2.0-bin is already the newest version.
libgtk2.0-common is already the newest version.
g++ is already the newest version.
Package libgtkmm-2.4-1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgtkmm-2.4-1c2a
E: Package libgtkmm-2.4-1 has no installation candidate
beni@Miranda:~$


---

### Post by johannes on 2006-06-01
> However the following packages replace it:
libgtkmm-2.4-1c2a

```
sudo apt-get install libgtkmm-2.4-1c2a
```

---

