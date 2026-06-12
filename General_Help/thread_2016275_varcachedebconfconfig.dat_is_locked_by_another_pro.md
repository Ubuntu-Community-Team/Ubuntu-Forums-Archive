---
title: "/var/cache/debconf/config.dat is locked by another process"
date: 2012-07-04
forum: General Help
---

### Post by artofshred87 on 2012-07-04
can somone help me get rid of this  sandboxgamemaker error it keeps popping up and i dont know how to kill it

aos87@ubuntu:~$ sudo apt-get install software-center
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
aos87@ubuntu:~$ sudo dpkg --configure -a
Setting up sandboxgamemaker (2.6.1+dfsg-7) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing sandboxgamemaker (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sandboxgamemaker
aos87@ubuntu:~$ sudo dpkg --configure -a
Setting up sandboxgamemaker (2.6.1+dfsg-7) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing sandboxgamemaker (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sandboxgamemaker

---

### Post by msammels on 2012-07-04
Hey art,

Check out [this thead](http://ubuntuforums.org/showthread.php?p=9373383).

---

### Post by jmfal on 2012-07-04
Hi artofshred87

Try rebooting and at the grub screen select the recovery kernal.

From the menu  click on ---  dpkg  fix broken packages.

Follow the prompts and answer the question>>> y/n>>y, press enter

Ubuntu may ask to enter a command problalby this one:

```
  sudo dpkg --configure  -a    
```

To get to the grub screen, at the enter bios/setup screen hold down the shift key till the grub screen appears, use up/down arrows to make selection, press enter,, ssame goes for the menu in recovery.

---

### Post by artofshred87 on 2012-07-04
tried installing sudo apt-get install nautilus-open-terminal
and got this error

aos87@ubuntu:~$ sudo apt-get install nautilus-open-terminal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nautilus-open-terminal is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'nautilus-open-terminal' has no installation candidate
aos87@ubuntu:~$ sudo apt-get install nautilus-open-terminal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nautilus-open-terminal
0 upgraded, 1 newly installed, 0 to remove and 231 not upgraded.
1 not fully installed or removed.
Need to get 63.1 kB of archives.
After this operation, 918 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe nautilus-open-terminal amd64 0.19-1build1 [63.1 kB]
Fetched 63.1 kB in 3s (20.6 kB/s)                 
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Selecting previously deselected package nautilus-open-terminal.
(Reading database ... 
dpkg: warning: files list file for package `sandboxgamemaker' missing, assuming package has no files currently installed.
(Reading database ... 168901 files and directories currently installed.)
Unpacking nautilus-open-terminal (from .../nautilus-open-terminal_0.19-1build1_amd64.deb) ...
Processing triggers for gconf2 ...
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up nautilus-open-terminal (0.19-1build1) ...
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

any thoughts ive tried so many things at this point nothings worrked maybe some tough love!

---

### Post by jmfal on 2012-07-04
Try running this:

```
  sudo apt-get install --fix-missing   
```

If that doesn't help try:

```
    sudo apt-get install -f  
```

---

### Post by dino99 on 2012-07-04
"locked by another process" means that an other updating soft is already loaded, like synaptic or update-manager. This error is saying: only use one at the same time, so close the other(s)

---

### Post by artofshred87 on 2012-07-05
hi jmfal i ran the first code you suggested and this i what i got 

aos87@ubuntu:~$ sudo apt-get install --fix-missing
[sudo] password for aos87: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

