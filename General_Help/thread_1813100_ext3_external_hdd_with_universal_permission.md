---
title: "ext3 external hdd with universal permission"
date: 2011-07-27
forum: General Help
---

### Post by jayanthan on 2011-07-27
A friend of mine and I bought an external hd (WD Elements 2TB) and formatted it in ext3 as root. Now we want to use this hard disk in more than one systems with different usernames. So we did 
"chmod -R 777 /media/VolumeLabel"
in all the systems.
But we want the hd to pass around. So its a little bit inconvenient to do chmod all the time. So what should we do to make the access for the hd universal in all the systems that we plug it in?

---

### Post by vanadium on 2011-07-27
Create a directory on that drive, change permissions of that directory to 777. Then any users will be able to fully use that directory irrespective of the permissions of the mount point (as long as that still allows read execute permissions for others, but that is pretty standard).

---

### Post by jayanthan on 2011-07-27
nice. works well!

---

### Post by Marzata on 2012-05-21
This is a very good idea. Thank you!

---

