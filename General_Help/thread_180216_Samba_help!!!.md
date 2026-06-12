---
title: "Samba help!!!"
date: 2006-05-21
forum: General Help
---

### Post by JohnnyHaff on 2006-05-21
i'm trying to install smbfs ...  i'm following this guide... [http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)  When i type the code: sudo apt-get install smbfs i get error messages that say  
"Err [http://ubuntu-backports.morrormax.net](http://ubuntu-backports.morrormax.net) hoary-backports/universe Packages
404 Not Found"

any ideas??  i get the same message for each, universe, multiverse, restricted, and main...   i dunno what to do.  imma newbie tryin to figure this stuff out. ](*,)

---

### Post by kzutter on 2006-05-21
Sounds like your /etc/apt/sources.list is messed up

First, I think it is mirrormax.net  not morrowmax.net

and why do you need this hoary backports repository anyway?

smbfs is in breezy main.

If you want additional help, you should post your sources.list

---

### Post by jones_jj on 2006-05-21
Another way to install Samba is to use synaptec.  **System->Administration->Synaptec**.  From there just scroll through the list (or just start typing samba) and mark the package for install, and it will pull other packages that it needs to complete the install.  Then you should have Samba installed.

---

