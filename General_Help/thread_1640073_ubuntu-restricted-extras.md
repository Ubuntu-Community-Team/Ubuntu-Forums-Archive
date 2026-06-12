---
title: "ubuntu-restricted-extras"
date: 2010-12-07
forum: General Help
---

### Post by jon zendatta on 2010-12-07
I have a clean install. Have added medibuntu to source list, but cannot add the medibutu key
```
wget --quiet http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add -


``` no response & no Ok.
When I attempt to install ubuntu-restricted-extras, it just hangs and doesn't connect to sourceforge.

---

### Post by wojox on 2010-12-07
You really don't need medibuntu.

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

---

### Post by jon zendatta on 2010-12-07
```
GPG error: http://packages.medibuntu.org maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
:KS

---

### Post by jon zendatta on 2010-12-07
i tried this
```
sudo dpkg --configure -a
```
it hangs at adobe flash player

---

### Post by wojox on 2010-12-07
Go into Software Sources > Other Software and remove medibuntu.

Close all package management programs (Synaptic Software Center) and run that command in the terminal again.

---

### Post by tajiknomi on 2010-12-07
> **jon zendatta said:**
> ```
GPG error: http://packages.medibuntu.org maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```:KS

[SIZE=2]try this command:-

[/SIZE]```
[COLOR=#000000][FONT=Times New Roman]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783[/FONT][/COLOR]
```

[SIZE=2]Then sudo apt-get update....[/SIZE]

---

### Post by jon zendatta on 2010-12-07
Ok I cancelled medibuntu and did ```
sudo dpkg --configure -a
``` but it doesn't connect to sourceforge.

---

### Post by jon zendatta on 2010-12-07
would it make any difference, if I did another clean install?

---

### Post by tajiknomi on 2010-12-07
> **jon zendatta said:**
> would it make any difference, if I did another clean install?

[SIZE=2]Have you tried the command above in my post...?whats the output of that...?

also try > [/SIZE]```
[SIZE=3]rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```[/SIZE]

---

### Post by wojox on 2010-12-07
> **jon zendatta said:**
> Ok I cancelled medibuntu and did ```
sudo dpkg --configure -a
``` but it doesn't connect to sourceforge.

The command from post #2.

---

### Post by jon zendatta on 2010-12-07
thanks for your help Wojox, but i can't run that command. Off to work now so I'll try again in 10 hours

---

### Post by jon zendatta on 2010-12-08
Still no go.
```
rm /var/lib/dpkg/lock
rm: remove write-protected regular empty file `/var/lib/dpkg/lock'? 

```
```
sudo dpkg --configure -a
dpkg: status database area is locked by another process

```
here is my source list
```
deb http://nz.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid universe
deb http://nz.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

## Medibuntu - Ubuntu 10.10 "maverick meerkat"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ maverick free non-free
deb-src http://packages.medibuntu.org/ maverick free non-free
```

---

### Post by jon zendatta on 2010-12-08
As I stated I cannot load the medibuntu key:KS

---

### Post by lykeion on 2010-12-08
Error messages about dpkg locked by another process means that you have several package managers running. 
You need to close down all of them before launching any dpkg-related commands.
So before you try anything else:
**Close all package managers like Synaptic, Update Manager, Ubuntu Software Center, etc !!!**

Secondly, what are you trying to achieve? The post title says ubuntu-restricted-extras but then you are trying to add the medibuntu repositories?
EDIT:
Saw that you started a thread about "install restricted-extras" in [august 2010]("http://ubuntuforums.org/showthread.php?t=1549412") and that you succeeded to install it, so please explain what you're having problem with.

How to install ubuntu-restricted-extras
[LIST]
[*]Close down all package managers (Synaptic, Update Manager, Ubuntu Software Center, etc)
[*]Start Ubuntu Software Center (Applications > Ubuntu Software Center)
[*]In search field enter "ubuntu restricted" and install "Ubuntu restricted extras" package
[/LIST]
How to add the medibuntu repositories:
[LIST]
[*]Read this: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[/LIST]

---

