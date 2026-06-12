---
title: "Fstab &quot;exec&quot; not working"
date: 2010-11-08
forum: General Help
---

### Post by Cluadia C on 2010-11-08
Hiya!

I'm struggling to figure out what is wrong with my fstab parameters here as to figure out why "exec" isn't working.  

> /dev/sda4                                  /media/Boa-Tarde ntfs  nls=iso8859-1,rw,users,umask=005,gid=boa,user,owner,noatime,nodiratime,exec,uid=1000         0  0 

I'm using kubuntu 10.10.   

Its also possible this might be a weird Wine associated conflict :D   I'm using Wine 1.2.1, and this is the error I am getting when trying to run programs off the ntfs drive, which started sometime after upgrading from 10.04.   Programs which worked fine on that drive are now giving this error:

> err:virtual:map_image failed to set 60000020 protection on section .text, noexec filesystem?


Any help, whether it be direct or simply pointing me to the right direction as to what to search for is very much humbly appreciated  :D

---

### Post by Cluadia C on 2010-11-12
**Solved**
This problem was indeed Wine related.     The solution for me was to simply create a new wine folder.  This was achieved by simply renaming .wine in the home folder to .wine2 (or whatever you want), and creating a new .wine.

---

