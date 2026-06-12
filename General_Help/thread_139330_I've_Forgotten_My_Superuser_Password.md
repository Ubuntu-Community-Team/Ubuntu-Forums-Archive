---
title: "I've Forgotten My Superuser Password"
date: 2006-03-03
forum: General Help
---

### Post by Mark76 on 2006-03-03
Though I can't say I remember ever having one.   Nevertheless I need it to install openmotif.

Can anyone give me a hint as to where it might be?

---

### Post by joshuapurcell on 2006-03-03
You can change the password by booting up with the recovery mode kernel (hit ESC at the GRUB menu), then this command:```
passwd
```

---

### Post by Mark76 on 2006-03-03
> mark-williams@098786weq:~$ dpkg -i openmotif_2.1.30-5_i386.deb
dpkg: requested operation requires superuser privilege
mark-williams@098786weq:~$


How do I activate superuser?

---

### Post by jdong on 2006-03-03
The superuser is accessed through the **sudo** command.

Please see the following Ubuntu Wiki article for more details: [https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

---

### Post by Mark76 on 2006-03-03
I know my sudo password. So why can't I depackage the stupid file? :mad:

---

### Post by jdong on 2006-03-03
What output does **sudo** dpkg -i openmotif_2.1.30-5_i386.deb produce?

---

### Post by Mark76 on 2006-03-03
> mark-williams@098786weq:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
mark-williams@098786weq:~$


It didn't ask for my password

---

### Post by Mark76 on 2006-03-03
This

> mark-williams@098786weq:~$ sudo dpkg -i openmotif_2.1.30-5_i386.deb
Password:
dpkg: error processing openmotif_2.1.30-5_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 openmotif_2.1.30-5_i386.deb
mark-williams@098786weq:~$


---

### Post by Qrk on 2006-03-03
You must be using sudo like su ... that is, opening a root session in the terminal with it. Sudo must be used in front of every command you want to run as root. (if you want your root powers to stick, use sudo su)

so don't do:
```
sudo
command
```

but 
```
sudo command
```

---

### Post by Mark76 on 2006-03-03
Isn't that what I did?

---

### Post by Qrk on 2006-03-03
> mark-williams@098786weq:~$ sudo dpkg -i openmotif_2.1.30-5_i386.deb
Password:
dpkg: error processing openmotif_2.1.30-5_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
openmotif_2.1.30-5_i386.deb
mark-williams@098786weq:~$

You have to cd to the directory where you have the file as well. So if it is on your desktop, you type

```
cd ~/Desktop
sudo dpkg -i packagename.deb
```

Remember you can use tab to complete the name of the file once you start typing it.

---

### Post by Mark76 on 2006-03-03
mark-williams@098786weq:~$ sudo  dpkg -i openmotif_2.1.30-5_i386.deb
dpkg: error processing openmotif_2.1.30-5_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 openmotif_2.1.30-5_i386.deb
mark-williams@098786weq:~$

---

### Post by Mark76 on 2006-03-03
mark-williams@098786weq:~$ cd ~/desktop
bash: cd: /home/mark-williams/desktop: No such file or directory
mark-williams@098786weq:~$ cd
mark-williams@098786weq:~$ cd ~/Desktop
mark-williams@098786weq:~/Desktop$ sudo dpkg -i packagename.deb
dpkg: error processing packagename.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 packagename.deb
mark-williams@098786weq:~/Desktop$
mark-williams@098786weq:~/Desktop$ sudo dpkg -i packagename.deb
dpkg: error processing packagename.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 packagename.deb
mark-williams@098786weq:~/Desktop$

---

### Post by Mark76 on 2006-03-03
WHY IS NOTHING WORKING!? :mad:

---

### Post by Qrk on 2006-03-03
Where is the .deb package? Chances are its on your desktop, because that is where Firefox downloads things to by default. 

Make sure the file is in the directory you are looking at by typing 

```
ls
```

Also, I used packagename.deb as an example, you need to actually type in the name of the package.

---

### Post by majikstreet on 2006-03-03
Try filling in the package name... here's what you need to do
```

cd ~/Desktop
sudo dpkg -i openmotif_2.1.30-5_i386.deb

```

---

### Post by Mark76 on 2006-03-03
It's in my home folder

---

### Post by Mark76 on 2006-03-03
mark-williams@098786weq:~$ cd ~/home
bash: cd: /home/mark-williams/home: No such file or directory
mark-williams@098786weq:~$

---

### Post by Qrk on 2006-03-03
And you are absolutely sure you are in there too? Just to make sure... do this:

```
cd ~/
ls
sudo dpkg -i openmotif_2.1.30-5_i386.deb
```

if it doesn't work paste the whole output up here.

~/ is home, you don't need to type home in. (~ means /home/user)

---

### Post by Mark76 on 2006-03-03
Okay.  I think I might have already have had it

> mark-williams@098786weq:~$ sudo dpkg -i openmotif_2.1.30-5_i386.deb
(Reading database ... 93493 files and directories currently installed.)
Unpacking openmotif (from openmotif_2.1.30-5_i386.deb) ...
dpkg: error processing openmotif_2.1.30-5_i386.deb (--install):
 trying to overwrite `/etc/menu-methods/mwm-menumethod', which is also in package lesstif-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 openmotif_2.1.30-5_i386.deb


---

### Post by Qrk on 2006-03-03
hmm, you might find what you are looking for in:

```
sudo apt-get install libmotif-dev
```

---

