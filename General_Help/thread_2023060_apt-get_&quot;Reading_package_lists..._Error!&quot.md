---
title: "apt-get &quot;Reading package lists... Error!&quot;"
date: 2012-07-11
forum: General Help
---

### Post by CLCressman on 2012-07-11
I am running Precise.

I tried ```
sudo apt-get update
``` and I get this message ```
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

```While searching the forum I tried ```
 sudo rm /var/lib/dpkg/lock
``` and```
sudo rm /var/lib/apt/lists/* -rf
```then```
sudo apt-get update
```No luck, so I tried ```
chester@Green:~$ sudo rm /etc/group.lock
[sudo] password for chester: 
rm: cannot remove `/etc/group.lock': No such file or directory
chester@Green:~$ sudo rm /etc/gshadow.lock
rm: cannot remove `/etc/gshadow.lock': No such file or directory
chester@Green:~$ sudo rm /etc/passwd.lock
rm: cannot remove `/etc/passwd.lock': No such file or directory
chester@Green:~$ sudo apt-get autoremove
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

```I found this on two threads, so maybe I didn't do it all in the right order. 

Thanks in advance.

---

### Post by CLCressman on 2012-07-19
This thread ([http://ubuntuforums.org/showthread.php?t=2023794](http://ubuntuforums.org/showthread.php?t=2023794)) describes the root of the problem and the solution.

---

