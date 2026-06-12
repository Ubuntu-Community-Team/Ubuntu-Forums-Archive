---
title: "Don't know how to list a valid directory"
date: 2011-08-08
forum: General Help
---

### Post by GuitarGeek on 2011-08-08
i'm trying to install the firestorm linux viewer for second life. Everything is good when i run script untill is asks me where to put it. i cant list any valid directories -.-

this is what i get:

Enter the desired installation directory [/opt/secondlife-install]:


any examples on what to list without going into rocket science :o

---

### Post by GuitarGeek on 2011-08-08
any at all ._.

---

### Post by GuitarGeek on 2011-08-08
i already made a thread but absolutely noone posted an answer. It's a very simple question and i know it's a very simple answer.  how do i list a valid directory when given this



this is what i get:

Enter the desired installation directory [/opt/secondlife-install]:



 		                   		  		  		  		  		  	   	
	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11131905")

---

### Post by Basher101 on 2011-08-08
Do it with your terminal.```
sudo su
```then enter your password to be root (note don't try anything stupid, as you can delete now important systemfiles, just follow my commands), then you type ```
cp /opt/secondlife-install
``` and ```
ls -all
``` that will list all files and folders (hidden ones are marked with a . infront of the name, .mozilla for example)

---

### Post by GuitarGeek on 2011-08-08
alright i did that. but then i get this 

ls: cannot access .gvfs: Permission denied
total 180
drwxr-xr-x 30 linto linto  4096 2011-08-08 19:14 .
drwxr-xr-x  3 root  root   4096 2011-08-08 18:14 ..
drwx------  3 linto linto  4096 2011-08-08 19:14 .adobe
-rw-------  1 linto linto    60 2011-08-08 18:49 .bash_history
-rw-r--r--  1 linto linto   220 2011-08-08 18:14 .bash_logout
-rw-r--r--  1 linto linto  3353 2011-08-08 18:14 .bashrc
drwx------ 11 linto linto  4096 2011-08-08 21:57 .cache
drwx------  3 linto linto  4096 2011-08-08 18:32 .compiz
drwxr-xr-x  9 linto linto  4096 2011-08-08 19:05 .config
drwx------  3 linto linto  4096 2011-08-08 18:19 .dbus
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Desktop
-rw-r--r--  1 linto linto   100 2011-08-08 19:14 .dmrc
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Documents
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Downloads
drwx------  6 linto linto  4096 2011-08-08 18:51 .e16
-rw-------  1 linto linto    16 2011-08-08 18:19 .esd_auth
-rw-r--r--  1 linto linto   179 2011-08-08 18:14 examples.desktop
drwxr-xr-x  2 linto linto  4096 2011-08-08 19:34 .fontconfig
drwx------  4 linto linto  4096 2011-08-08 19:14 .gconf
drwx------  2 linto linto  4096 2011-08-08 21:58 .gconfd
-rw-r-----  1 linto linto     0 2011-08-08 18:44 .gksu.lock
drwx------  8 linto linto  4096 2011-08-08 21:56 .gnome2
drwx------  2 linto linto  4096 2011-08-08 18:33 .gnome2_private
-rw-r--r--  1 linto linto   137 2011-08-08 19:14 .gtk-bookmarks
d?????????  ? ?     ?         ?                ? .gvfs
-rw-------  1 linto linto  1590 2011-08-08 19:14 .ICEauthority
drwxr-xr-x  2 linto linto  4096 2011-08-08 19:04 .icons
drwxr-xr-x  3 linto linto  4096 2011-08-08 18:19 .local
drwx------  3 linto linto  4096 2011-08-08 19:14 .macromedia
drwx------  4 linto linto  4096 2011-08-08 18:50 .mozilla
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Music
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 .nautilus
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Pictures
-rw-r--r--  1 linto linto   675 2011-08-08 18:14 .profile
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Public
drwx------  2 linto linto  4096 2011-08-08 19:02 .pulse
-rw-------  1 linto linto   256 2011-08-08 18:19 .pulse-cookie
-rw-r--r--  1 linto linto     0 2011-08-08 18:44 .sudo_as_admin_successful
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Templates
drwxr-xr-x  2 linto linto  4096 2011-08-08 19:04 .themes
drwx------  4 linto linto  4096 2011-08-08 19:04 .thumbnails
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Videos
-rw-------  1 linto linto  5860 2011-08-08 21:58 .xsession-errors
-rw-------  1 linto linto 13801 2011-08-08 19:13 .xsession-errors.old
root@ubuntu:/home/linto# sudo su
root@ubuntu:/home/linto# cp /opt/secondlife-install
cp: missing destination file operand after `/opt/secondlife-install'
Try `cp --help' for more information.
root@ubuntu:/home/linto# ls -all
ls: cannot access .gvfs: Permission denied
total 180
drwxr-xr-x 30 linto linto  4096 2011-08-08 19:14 .
drwxr-xr-x  3 root  root   4096 2011-08-08 18:14 ..
drwx------  3 linto linto  4096 2011-08-08 19:14 .adobe
-rw-------  1 linto linto    60 2011-08-08 18:49 .bash_history
-rw-r--r--  1 linto linto   220 2011-08-08 18:14 .bash_logout
-rw-r--r--  1 linto linto  3353 2011-08-08 18:14 .bashrc
drwx------ 11 linto linto  4096 2011-08-08 21:57 .cache
drwx------  3 linto linto  4096 2011-08-08 18:32 .compiz
drwxr-xr-x  9 linto linto  4096 2011-08-08 19:05 .config
drwx------  3 linto linto  4096 2011-08-08 18:19 .dbus
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Desktop
-rw-r--r--  1 linto linto   100 2011-08-08 19:14 .dmrc
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Documents
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Downloads
drwx------  6 linto linto  4096 2011-08-08 18:51 .e16
-rw-------  1 linto linto    16 2011-08-08 18:19 .esd_auth
-rw-r--r--  1 linto linto   179 2011-08-08 18:14 examples.desktop
drwxr-xr-x  2 linto linto  4096 2011-08-08 19:34 .fontconfig
drwx------  4 linto linto  4096 2011-08-08 19:14 .gconf
drwx------  2 linto linto  4096 2011-08-08 21:58 .gconfd
-rw-r-----  1 linto linto     0 2011-08-08 18:44 .gksu.lock
drwx------  8 linto linto  4096 2011-08-08 21:56 .gnome2
drwx------  2 linto linto  4096 2011-08-08 18:33 .gnome2_private
-rw-r--r--  1 linto linto   137 2011-08-08 19:14 .gtk-bookmarks
d?????????  ? ?     ?         ?                ? .gvfs
-rw-------  1 linto linto  1590 2011-08-08 19:14 .ICEauthority
drwxr-xr-x  2 linto linto  4096 2011-08-08 19:04 .icons
drwxr-xr-x  3 linto linto  4096 2011-08-08 18:19 .local
drwx------  3 linto linto  4096 2011-08-08 19:14 .macromedia
drwx------  4 linto linto  4096 2011-08-08 18:50 .mozilla
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Music
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 .nautilus
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Pictures
-rw-r--r--  1 linto linto   675 2011-08-08 18:14 .profile
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Public
drwx------  2 linto linto  4096 2011-08-08 19:02 .pulse
-rw-------  1 linto linto   256 2011-08-08 18:19 .pulse-cookie
-rw-r--r--  1 linto linto     0 2011-08-08 18:44 .sudo_as_admin_successful
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Templates
drwxr-xr-x  2 linto linto  4096 2011-08-08 19:04 .themes
drwx------  4 linto linto  4096 2011-08-08 19:04 .thumbnails
drwxr-xr-x  2 linto linto  4096 2011-08-08 18:19 Videos
-rw-------  1 linto linto  5860 2011-08-08 21:58 .xsession-errors
-rw-------  1 linto linto 13801 2011-08-08 19:13 .xsession-errors.old
root@ubuntu:/home/linto# 


i did the sudo su command and entered password too.

---

### Post by GuitarGeek on 2011-08-08
hm

---

### Post by fdrake on 2011-08-08
> **GuitarGeek said:**
> 
d????????? ? ? ? ? ? .gvfs


when you ls from outside the folder , you are sending a command to the folder to execute the ls on itself. when you enter the folder and do ls to .gvfs , there is an error because it does not have permission and ownership.
to correct the problem from ROOT do:

chgrp -R adm .gvfs
chmod -R 755 .gvfs
so that all admin user will be able to use it

---

### Post by GuitarGeek on 2011-08-08
chgrp: cannot access `.gvfs': Permission denied


i don't think it wants me to install it

---

### Post by Basher101 on 2011-08-08
did you type sudo infront of it? sudo will prompt you for root password so you can apply it.
so the above mentioned commands must look like this:
sudo chgrp -R adm .gvfs
sudo chmod -R 755 .gvfs

---

### Post by fdrake on 2011-08-08
> **GuitarGeek said:**
> chgrp: cannot access `.gvfs': Permission denied


i don't think it wants me to install it

you have to maek sure u are root or use sudo infront of it. alson try chown first. that may be the problem since you dont have an owner yet.
do first this
--------------------
sudo su
chown -R root .gvfs
--------------------

than apply the other commands...

if that does not work do:
---------------------------------------
sudo su
chown -R root /home/linto
-----------------------------------------
probably doing the command externally will be easier.

---

### Post by Ad1217 on 2011-08-08
> **GuitarGeek said:**
> 
this is what i get:

Enter the desired installation directory [/opt/secondlife-install]: 	 	 		  		 			 	

you should be able to press enter to accept the default (/opt/secondlife-install)

or you could put */path/to/some/directory* if you want to put it somewhere else. However, I would not suggest doing this as you may have to change your path...

---

### Post by GuitarGeek on 2011-08-08
> **fdrake said:**
> you have to maek sure u are root or use sudo infront of it. alson try chown first. that may be the problem since you dont have an owner yet.
do first this
--------------------
sudo su
chown -R root .gvfs
--------------------

than apply the other commands...

if that does not work do:
---------------------------------------
sudo su
chown -R root /home/linto
-----------------------------------------
probably doing the command externally will be easier.

 both were permission denied.

---

### Post by GuitarGeek on 2011-08-08
> **Ad1217 said:**
> you should be able to press enter to accept the default (/opt/secondlife-install)

or you could put */path/to/some/directory* if you want to put it somewhere else. However, I would not suggest doing this as you may have to change your path...

  both said the directory doesn't exist.

---

### Post by Ad1217 on 2011-08-08
okay. try:

```
sudo mkdir /opt/secondlife-install
```
enter your password
then try running the install script again (also with sudo, by the way)

---

### Post by GuitarGeek on 2011-08-08
> **GuitarGeek said:**
> chgrp: cannot access `.gvfs': Permission denied


i don't think it wants me to install it

  asked me for pass.   then denied anyways.

---

### Post by Ad1217 on 2011-08-08
the output that you got from the previous command is not very helpful... the folder that you were trying to get to did not exist, so you are just doing ls on your home folder.
make sure that you have sudo privileges on your system. if it is shared, you will have to get permissions from your system administrator.

---

### Post by fdrake on 2011-08-09
from source [http://www.linuxforums.org/forum/red-hat-fedora-linux/139375-question-marks-ls.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/139375-question-marks-ls.html)
ok i did a little research and i found out that the fact of the ?????? showing on you permission means that may be a problem with the filesystem(possible data corruption). for some users the followin command worked (from regula user)

```
sudo chmod -R g+x .gvfs
```

if this still does not work i suggest you to do a reboot> press "shift"  key > select "root"> enter  "fsck" (check my hdd for errors and correct them). 

or simply try a live ubuntu cd. and make a copy that folder if it's possible.

---

### Post by Ad1217 on 2011-08-09
still: this DOES NOT MATTER. it is in your home folder. it has no relevance to the problem.

---

### Post by fdrake on 2011-08-09
> **Ad1217 said:**
> still: this DOES NOT MATTER. it is in your home folder. it has no relevance to the problem.

it doesn't matter where a file is located when the permissions are changes. i can create a file on your desktop, as a root with permission 700, and you still would never be able to read, edit or run it.

---

### Post by Ad1217 on 2011-08-09
my point is that this permissions issue has no relevance to the problem at all.

edit: though you are correct about the permissions, that is for a separate thread

---

### Post by Habitual on 2011-08-09
Enter the desired installation directory [/opt/secondlife-install]:

what happens if you press <enter>?

---

### Post by Starminn on 2011-12-11
Then it installs in /opt/secondlife-install and proceeds with installation.

```
robert@robert-Dell-DME510:~$ sudo ./Downloads/SecondLife-i686-3.2.1.244864/install.sh
[sudo] password for robert: 
Enter the desired installation directory [/opt/secondlife-install]: 
 - Installing to /opt/secondlife-install
 - Installing menu entries in /usr/local/share/applications
robert@robert-Dell-DME510:~$ 
```

---

