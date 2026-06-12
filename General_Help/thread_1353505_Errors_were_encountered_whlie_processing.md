---
title: "Errors were encountered whlie processing"
date: 2009-12-12
forum: General Help
---

### Post by MKVCrazy on 2009-12-12
[IMG]http://i48.tinypic.com/wwi7w5.png[/IMG]

also virtualbox-ose-source will stick at the very end of the error under "linux-image" too if I try to install VirtualBox. These errors happen after installation of some apps. What might be causing it?

OS: Ubuntu Server 9.10 64-Bit (GUI installed)

---

### Post by NoaHall on 2009-12-12
Can you post the output of ```
cat /etc/apt/sources.list
``` and ```
sudo ldconfig && sudo dpkg --configure -a
```

---

### Post by MKVCrazy on 2009-12-12
> **NoaHall said:**
> Can you post the output of ```
cat /etc/apt/sources.list
``` and ```
sudo ldconfig && sudo dpkg --configure -a
```

first command
```
root@XXXXX:~# cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mir1.ovh.net/ubuntu/ karmic main restricted contrib non-free
deb-src http://mir1.ovh.net/ubuntu/ karmic main restricted contrib non-free

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mir1.ovh.net/ubuntu/ karmic-updates main restricted
deb-src http://mir1.ovh.net/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mir1.ovh.net/ubuntu/ karmic universe
deb-src http://mir1.ovh.net/ubuntu/ karmic universe
deb http://mir1.ovh.net/ubuntu/ karmic-updates universe
deb-src http://mir1.ovh.net/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mir1.ovh.net/ubuntu/ karmic multiverse
deb-src http://mir1.ovh.net/ubuntu/ karmic multiverse
deb http://mir1.ovh.net/ubuntu/ karmic-updates multiverse
deb-src http://mir1.ovh.net/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mir1.ovh.net/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://mir1.ovh.net/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
root@XXXXX:~#
```

2nd command

```
root@XXXXX:~# ldconfig && sudo dpkg --configure -a
dpkg: status database area is locked by another process
root@XXXXX:~# 
```

---

### Post by NoaHall on 2009-12-12
The last command need a sudo in front of ldconfig.

---

### Post by MKVCrazy on 2009-12-12
> **NoaHall said:**
> The last command need a sudo in front of ldconfig.
Same message. I'm running as root.

---

### Post by NoaHall on 2009-12-12
> **MKVCrazy said:**
> Same message. I'm running as root.

Hm, close everything, and try again.

If it's still the same message then -> Go to "Software Sources" and change to the default sources - it might be because you're using servers different from default.

---

### Post by MKVCrazy on 2009-12-12
I've restarted and it shows nothing after typing the last command.

```
root@XXXXX:~# sudo ldconfig && sudo dpkg --configure -a
root@XXXXX:~#
```

---

### Post by MKVCrazy on 2009-12-12
Is it me or **VirtualBox OSE** is removed from repositories?

EDIT: Yes, server settings wrong!

---

### Post by MKVCrazy on 2009-12-13
I give up on the OSE version now I am trying to install the non-free one. But there's a compilation problem. It will not compile to start VBox because the kernel source dir is not right.

It's linking at
```
/lib/modules/2.6.32-xxxx-std-ipv6-64/build **OR**
/lib/modules/2.6.32-xxxx-std-ipv6-64/source
```

but the kernel I want to point is at
```
/lib/modules/2.6.31-16-generic/build
```

In the Terminal the DKMS usage is as follow
```
# /usr/sbin/dkms [action] [kernelsourcedir=source-directory]
```

so I entered
```
# /usr/sbin/dkms --kernelsourcedir=/lib/modules/2.6.31-16-generic/build
```

I also tried the following
```
# /usr/sbin/dkms build --kernelsourcedir=/lib/modules/2.6.31-16-generic/build
```

Nothing changes, I keep seeing that error in the vbox-install.org file.

**How can I change the setting where it link and look for kernel option?**

---

