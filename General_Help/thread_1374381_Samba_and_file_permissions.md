---
title: "Samba and file permissions"
date: 2010-01-06
forum: General Help
---

### Post by mcgrmic2 on 2010-01-06
I can't figure out if this should go in Networking or Security, so it's going here.

I have a Samba file share server on "server1" and 5 desktops/laptops that are mapped to my share drives. I have two users, "usera" and "userb". Both users have their own folder on one of the mapped drives. These folders have only read/write privileges for their respective owner with folder "usera" having owners of "usera:usera". Same for "userb".
On 4 of my computers, all privileges are working as they are supposed to. But on one, it swaps them. "usera" has "userb:userb" and visa versa. Why?

I turned off all desktops, reissued a chown command on the server for both files, then turned on and remapped all computers. Same computer still swapping the two. "userb" can access all of "usera"'s files.

---

