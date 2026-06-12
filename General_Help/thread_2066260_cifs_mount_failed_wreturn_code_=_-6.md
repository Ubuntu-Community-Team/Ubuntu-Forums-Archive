---
title: "cifs_mount failed w/return code = -6"
date: 2012-10-04
forum: General Help
---

### Post by floorripper on 2012-10-04
Hello,

I am having the same issue, I am not able tomount one type of windows share. I think it is a new one, because this share point has also the web-interface. I am not the administrator, so I do not know the details about this box.


```
mount -t cifs //sps02.austria.local/sites/sp03/Dokumentation -o username=majo,dom=MyDomain,password=MyPassword /mnt/a1-asfshare

```retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

dmesg#
[10826.686540]  CIFS VFS: cifs_mount failed w/return code = -6

In the windows it is possible to open it normally, via the explorer or run prompt:
```
\\sps02.austria.local\sites\sp03\dokumentation

```$ ping sps02.austria.local
PING sps02.austria.local (10.2.32.3) 56(84) bytes of data.
64 bytes from sps02.austria.local (10.2.32.3): icmp_seq=1 ttl=122 time=6.85 ms

---

### Post by albandy on 2012-10-04
I think is an auth protocol problem with cifs and new ntlm versions.
Take a look to this thread:
[https://bugzilla.samba.org/show_bug.cgi?id=8046](https://bugzilla.samba.org/show_bug.cgi?id=8046)

---

