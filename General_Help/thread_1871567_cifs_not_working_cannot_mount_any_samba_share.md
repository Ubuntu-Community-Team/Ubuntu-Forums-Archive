---
title: "cifs not working: cannot mount any samba share"
date: 2011-10-29
forum: General Help
---

### Post by pieroxy on 2011-10-29
Since a couple of days - after doing an update - I can't mount any Samba share anymore. Here is what happens:

```
pieroxy@pieroxy-dev:~$ sudo mount -v -t cifs //192.168.1.26/videos /media/movies 
Password: 
mount.cifs kernel mount options: ip=192.168.1.26,unc=\\192.168.1.26\videos,,ver=1,user=root,pass=********

```
And it just hangs there forever. At least, for more than 48 hours.

Things of interest:
- I enter no password as my share are public
- It worked before the upgrade of my machine
- Same result on a share from WinXP machine and a share from another Ubuntu machine (Samba)
- My machine is 11.04 not yet upgraded to 11.10


Does anyone have any idea how I can troubleshoot this?

---

### Post by pieroxy on 2011-10-29
I installed 11.10 and things are working. Something must have gotten rotten with my previous install.

---

