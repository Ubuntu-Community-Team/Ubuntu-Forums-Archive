---
title: "how do i uninstall ninja?"
date: 2010-06-17
forum: General Help
---

### Post by monsta1976 on 2010-06-17
i was following an online guide on ninja, i got distracted and closed terminal now i cant download anything i just get "Errors were encountered while processing: 
 ninja" 

how do i remove ninja?

---

### Post by doas777 on 2010-06-17
so did it install correctly, or is apt stuck?

if apt is stuck, try
```
sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by monsta1976 on 2010-06-17
it never installed properly now it wont uninstall!

---

### Post by bodhi.zazen on 2010-06-17
Moved to general help.

Please post the exact error message you are getting.

---

### Post by monsta1976 on 2010-06-17
installArchives() failed: W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages) 
Selecting previously deselected package unace. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 128852 files and directories currently installed.) 
Unpacking unace (from .../archives/unace_1.2b-7_i386.deb) ... 
Processing triggers for man-db ... 
Setting up ninja (0.1.3-1) ... 
Starting ninja: log: reading configuration file: /etc/ninja/ninja.conf 
log: ninja version 0.1.3 initializing 
log: magic group: gid=0 (root) 
log: logfile: /var/log/ninja.log 
die: error: `/var/log/ninja.log' is not a regular file 
invoke-rc.d: initscript ninja, action "start" failed. 
dpkg: error processing ninja (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up unace (1.2b-7) ... 
Errors were encountered while processing: 
 ninja

---

### Post by monsta1976 on 2010-06-17
oh and

E: ninja: subprocess installed pre-removal script returned error exit status 1

when i try to uninstall

---

### Post by bodhi.zazen on 2010-06-17
Try;

```
sudo touch /var/log/ninja.log
sudo apt-get install ninja
sudo apt-get purge ninja
sudo rm /var/log/ninja.log
```

I would also file a bug report against ninja on launchpad

---

### Post by eddier on 2010-08-24
Damn! I've run into the same problem..

```
(Reading database ... 144255 files and directories currently installed.)

Removing ninja ...

Stopping ninja: invoke-rc.d: initscript ninja, action "stop" failed.

dpkg: error processing ninja (--remove):

 subprocess installed pre-removal script returned error exit status 1

Starting ninja: log: reading configuration file: /etc/ninja/ninja.conf

die: error: unable to read configuration file

invoke-rc.d: initscript ninja, action "start" failed.

dpkg: error while cleaning up:

 subprocess installed post-installation script returned error exit status 1

Errors were encountered while processing:

 ninja
```

Tried the commands given by Bodhi.zazen but the stupid thing is still there...HEEEELP.:confused:

eddier

---

### Post by sttal on 2011-02-07
I had the same problem !!the solution is to:
create a text file called "ninja.c" with the folowing:

int main(){
return 0;
}

The next step is to compile it with gcc with command:
$ gcc ninja.c -o ninja

then go to the /usr/sbin directory and substitute the ninja there with the on created by the gcc

finally: sudo apt-get purge ninja

---

### Post by duke.tim on 2012-03-09
I don't mean to revive an old thread but am posting an alternative method of solving this, rather than compiling a binary.

I recently ran into the same problem 

bodhi.zazen instructions  + changing the init script

> sudo touch /var/log/ninja.log
sudo apt-get install ninja


Then > Open Terminal ( Accessories -> Terminal )

Type sudo gedit /etc/init.d/ninja

Immediately after the line PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

type 'exit 0' without the quotes.

Save

[http://scrollsofvipin.blogspot.com/2010/06/how-to-uninstall-ninja-privilege.html](http://scrollsofvipin.blogspot.com/2010/06/how-to-uninstall-ninja-privilege.html)
and finally 

> sudo apt-get purge ninja
sudo rm /var/log/ninja.log

Probably caused by not configuring it before you wanted to remove.

---

