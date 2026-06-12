---
title: "samba only sees root ?"
date: 2012-06-23
forum: General Help
---

### Post by ulao on 2012-06-23
I use samba mainly for remote admin on my home system. So I log-in as an admin. I also allow root log-ins for trouble shooting. Though logging in as root still only allows me to see //myLinuxServer/root. When I brows the folder I see every folder I should but each folder complains about no rights. This seemed to happen from the latest Ubuntu upgrade. I tried to remove and re-install but no change. I dont see anything in the smb log file at all. Can anyone help ?

---

### Post by ulao on 2012-06-30
Could anyone drop a tip? Just dont know what to look for. The samba share shows the directory listing but no access to any of the folders? I set up webmin and everything looks good in there.

Ok I tried to create a share to var and that works, same for etc, but creating a share to / does not work. For remote admin needs I need to make a share to the root as I have for many years. Did Ubuntu make a change to this?

---

