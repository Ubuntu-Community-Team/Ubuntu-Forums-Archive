---
title: "Sharing problem"
date: 2009-11-30
forum: General Help
---

### Post by gretarsson on 2009-11-30
Hi I had ubuntu 8.10 and upgrade to 9.04 and after that I can not see me own sharing maps or no one else

---

### Post by Iowan on 2009-11-30
Sharing maps... as in Samba, NFS, both, or something else?
No one else... sees shares, or cannot be pinged?

---

### Post by gretarsson on 2009-12-01
> **Iowan said:**
> Sharing maps... as in Samba, NFS, both, or something else?
No one else... sees shares, or cannot be pinged?
It is in me network folder no sharing maps appear there but I can see me maps in samba "smb conf" folder, I have tried both eth1 and ethö connection still same

---

### Post by audiomick on 2009-12-01
Hallo.
I think I had the same problem.
try this:
[https://bugs.launchpad.net/hundredpapercuts/+bug/389909](https://bugs.launchpad.net/hundredpapercuts/+bug/389909)

This addresses an issue that has arisen with a function that more and more Internet Providers are using. I think it is called IP Redirection. It is a thing where if the DNS that your provider uses can't find the site you are looking for, it makes alternative suggestions. This messes up the thing that is looking for your shares. I am sorry my description is vague. I read a precise description of it somewhere about a month ago, but have no idea where...

If that doesn't do it, check out this thread:
[http://ubuntuforums.org/showthread.php?t=1169149&page=21](http://ubuntuforums.org/showthread.php?t=1169149&page=21)

It is a monster, but there is some really solid advice in there.

---

