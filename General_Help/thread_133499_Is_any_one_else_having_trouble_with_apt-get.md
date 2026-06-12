---
title: "Is any one else having trouble with apt-get?"
date: 2006-02-20
forum: General Help
---

### Post by capn_hector on 2006-02-20
so i just installed ubunu a couple of weeks ago and used apt-get just fine.  i went to get nmap today and got this

jeremy@ubuntu:~$ apt-get install nmap
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
jeremy@ubuntu:~$

also i cant sudo in or su since the root password is something i never set but is asked for.  (when did the root password get set durring the install?)

---

### Post by mishranurag on 2006-02-20
Did you have synaptic open while doing this? It appears that apt-get didn't get exclusive lock to install nmap.

By the way, what is nmap for?

Anurag

---

### Post by Robgould on 2006-02-20
It is becaus synaptic or something else is already using Apt to update.  Make sure synaptic is closed before you run apt.  If you have synaptic set up to auto-update it can be running in the background.

---

### Post by carlosqueso on 2006-02-20
Actually...try putting sudo before it and it should work i.e. ```
sudo apt-get install nmap
``` sudo just requires your user password.  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) has more information on it if you care.

---

### Post by carlosqueso on 2006-02-20
[QUOTE=mishranurag]

By the way, what is nmap for?

[/QUOTE]

The package description for nmap shows:

>  Nmap is a utility for network exploration or security auditing. It
 supports ping scanning (determine which hosts are up), many port
 scanning techniques, version detection (determine service protocols
 and application versions listening behind ports), and TCP/IP
 fingerprinting (remote host OS or device identification). Nmap also
 offers flexible target and port specification, decoy/stealth scanning,
 sunRPC scanning, and more. Most Unix and Windows platforms are
 supported in both GUI and commandline modes. Several popular handheld
 devices are also supported, including the Sharp Zaurus and the iPAQ.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
 

---

### Post by larsemil on 2006-02-20
yep. nmap is great for looking what ports are open on your friends computer...:evil:

---

### Post by capn_hector on 2006-02-20
ok thanks for the input.  the next question, (i have not looked in the wiki)  how to list and shutdown processes?  and ill try sudo asap.

---

### Post by capn_hector on 2006-02-21
ok a new problem.

jeremy@ubuntu:~$ sudo -i
Password:
root@ubuntu:~# apt-get install nmap
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nmap

the sudo worked but now what?


also bump

---

### Post by jrib on 2006-02-21
paste the contents of /etc/apt/sources.list, seems like you don't have the main repository enabled

---

### Post by carlosqueso on 2006-02-21
your sources.list should look like mine:

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```  You can edit it with ```
sudo gedit /etc/apt/sources.list
```

---

### Post by capn_hector on 2006-02-25
well i figured it out, i did not have teh "Universal" repository list (using the gui front end)  although i prefer to use the terminal how do i enable different repository's for apt-get?  (do i edit the sources.list??)

---

