---
title: "Why am asked to re-install Samba?"
date: 2012-02-05
forum: General Help
---

### Post by walterbyrd on 2012-02-05
I installed samba with:

```
# aptitude install samba
```

I get the following:

```
The following NEW packages will be installed:
  samba 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,084 kB of archives. After unpacking 23.5 MB will be used.
Get: 1 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main samba amd64 2:3.5.11~dfsg-1ubuntu2.1 [8,084 kB]
Fetched 8,084 kB in 19s (424 kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 181525 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.5.11~dfsg-1ubuntu2.1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up samba (2:3.5.11~dfsg-1ubuntu2.1) ...
Generating /etc/default/samba...
Importing account for nobody...ok
Importing account for walter...ok
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
smbd start/running, process 7013
nmbd start/running, process 7040
```


I made some changes to /etc/samba/smb.conf

I went to restart samba

```
# samba restart
```

and I get the message:

```
# The program 'samba' is currently not installed.  You can install it by typing:
# apt-get install samba4
```

WTF?

---

### Post by Rodney9 on 2012-02-05
I'm not sure about> aptitude install samba

> apt-get install samba4 is the correct way or use Synaptic.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by lisati on 2012-02-05
These days the daemons (background processes) for samba are named smbd and nmbd: it is these processes you will need to (re)start.

---

### Post by walterbyrd on 2012-02-06
Okay, so restart with the following?

```
# smbd restart
```
```
# nmbd restart
```

---

### Post by redmk2 on 2012-02-06
> **walterbyrd said:**
> Okay, so restart with the following?

```
# smbd restart
```
```
# nmbd restart
```

The incantation for root is```
service smbd restart 
service nmbd restart
```

Or from a non-root (sudoer) prompt```
sudo service smbd restart
sudo service nmbd restart
```

---

