---
title: "My Sql - debconf locked up!"
date: 2012-03-27
forum: General Help
---

### Post by uturniturn on 2012-03-27
I've opened a can of worms. I'm attempting to build a Wordpress site locally and have entered a world of MySql, Php and Apache2.

I may have mistakenly downloaded MySql on line instead of through Synaptic and now this: Can't upgrade, install or remove MySql now, i don't know how to clear the Apport MaxReports, where are they? Go slowly please!

source temporarily unavailable
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Unpacking linux-image-3.0.0-17-generic (from .../linux-image-3.0.0-17-generic_3.0.0-17.30_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb
 /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea's?

---

### Post by raja.genupula on 2012-03-27
hi open your terminal and do as 
```
sudo nautilus
```
a new window will opens then at that click at filesystem(left side). in that go to this location var->cache->debconf . in this location look for a file named with password . select and delete it . 

then close the window and in your terminal do as 
```
sudo apt-get install -f
```

let us know what you got . all the best .

---

### Post by uturniturn on 2012-03-27
Same again, i'm afraid,

 files list file for package `mysql-server-5.1' missing, assuming package has no files currently installed.
(Reading database ... 204986 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.61-0ubuntu0.11.10.1 (using .../mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by uturniturn on 2012-03-27
Further news...

No progress!

---

### Post by raja.genupula on 2012-03-27
have you deleted that file names as password and some extension in that location  ? 

here look at my post #21  and follow the instructions 
[http://ubuntuforums.org/showthread.php?t=1940228&page=3](http://ubuntuforums.org/showthread.php?t=1940228&page=3)

---

### Post by uturniturn on 2012-03-27
Raja, I thought i did exactly as you instructed i'll try your new help...

Thank you very much indeed.....speak soon...

---

### Post by uturniturn on 2012-03-27
Setting up mysql-common (5.1.61-0ubuntu0.11.10.1) ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 
dpkg: warning: files list file for package `mysql-server-5.1' missing, assuming package has no files currently installed.
(Reading database ... 204979 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.61-0ubuntu0.11.10.1 (using .../mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.61-0ubuntu0.11.10.1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.3.6-13ubuntu3.6_i386.deb) ...

Have i stopped this too quickly! I'll start again and take my time...more news to come Raja, you are a king of the internet for sure....i'll let you know...

---

### Post by raja.genupula on 2012-03-27
dont stop any of upgrade/install in middle , its not a good choice.

actually i have faced same situation now you have faced in past and  i have found a solution for the problems similar to this . 

thats what i have given to you .

---

### Post by uturniturn on 2012-03-27
matthew@matthew-ThinkPad-T60:~$ sudo su
[sudo] password for matthew: 
root@matthew-ThinkPad-T60:/home/matthew# fuser -v /var/cache/debconf/config.dat
                     USER PID ACCESS COMMAND
/var/cache/debconf/config.dat:
                     root       1290 F.... frontend
root@matthew-ThinkPad-T60:/home/matthew# 


Raja, Hi! so no real progress but when i run this command this information is returned. I have no idea what it means but maybe its helpful to a whizzkid like you?

I lose my patience so i'm going to see what happens with firebird but it still leaves me with this problem!!

---

### Post by raja.genupula on 2012-03-27
> **uturniturn said:**
> matthew@matthew-ThinkPad-T60:~$ sudo su
[sudo] password for matthew: 
root@matthew-ThinkPad-T60:/home/matthew# fuser -v /var/cache/debconf/config.dat
                     USER PID ACCESS COMMAND
/var/cache/debconf/config.dat:
                     root       1290 F.... frontend
root@matthew-ThinkPad-T60:/home/matthew# 


Raja, Hi! so no real progress but when i run this command this information is returned. I have no idea what it means but maybe its helpful to a whizzkid like you?

I lose my patience so i'm going to see what happens with firebird but it still leaves me with this problem!!

Hi i told you to follow post  21 there , did you ?

---

### Post by uturniturn on 2012-03-27
I did Raja, to no avail the file has four other files in it now:
Config.Dat
Config.Dat old
Templates.Dat
Templates.Dat old

Passwords was sent to the Rubbish Bin.

When i run Nautilus this error notice comes up before i get the option to see the File Options. I carried on with your instructions carefully.


e' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

--- Hash table keys for warning below:
--> l2049
--> inode/directory
--> root
(nautilus:15975): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///var
--> file:///

(nautilus:15975): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time (keys above)
Shutting down nautilus-gdu extension
Shutting down nautilus-image-converter extension

---

### Post by raja.genupula on 2012-03-28
you no need to worry about all those files man , trust me i did that on my system and suggested to you . please follow what i have given , do all those things carefully .

---

### Post by uturniturn on 2012-03-28
Gotcha, thank you Raja!

---

### Post by raja.genupula on 2012-03-28
aah! thats Good news , now please mark the thread as solved from thread tools .

---

