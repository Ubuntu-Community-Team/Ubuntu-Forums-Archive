---
title: "Issue Mounting CIFS Share"
date: 2010-11-30
forum: General Help
---

### Post by russjar on 2010-11-30
Hi all,

I'm trying to mount a share on a Windows 7 desktop from my Ubuntu build. the share I'm trying to connect to is the administrative share "C$". the command I'm entering is 

mount -t cifs //IP_Address/C$ -o username=domain_name\windows_username,password=windows_password /mnt/ntserver

and I am getting the following error

[B]mount error(111): Connection refused
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/B]

I did attempt this to another share (Temp) with everyone read access however I got the same error as above. The account I'm trying to authenticate is a local administrator of the Windows 7 build.

I'm not a Linux expert so be gentle

Thanks.

---

### Post by papibe on 2010-12-01
A couple of things:

The dollar sign ($) is an special character on bash, it maybe necessary to "escape it". Try this:
```
$ mount -t cifs //IP_Address/C\$ ... 
```

In order to mount samba shares on bash, you need an additional package besides samba. Check if it is install:
```
$ dpkg -l | grep smbfs
```
If it isn't install, get it like this:
```
$ sudo apt-get install smbfs
```
Good Luck!

---

### Post by RustySheriffsBadge on 2011-05-07
Hi,

I know this is a bit of an old post, but better late than never hey?

I managed to resolve similar issues connecting to the windows 7 admin shares (c$ d$ etc) from xubuntu 11.04.

The problem was with the windows machine, there is setting in the windows registry that prevents local network users connecting to the admin shares. You just have to put a new reg key in to fix it.

Key goes in:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System

Key DWORD (32-bit): LocalAccountTokenFilterPolicy
Key Value : 1

[Further information from Microsoft available here]("http://support.microsoft.com/kb/947232")  

Hope that helps :)

---

