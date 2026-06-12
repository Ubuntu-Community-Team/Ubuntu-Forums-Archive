---
title: "Renamed /var but where did it go?"
date: 2012-06-04
forum: General Help
---

### Post by nickdc on 2012-06-04
Just curious: still a lot to learn about linux!

Having a problem installing 12.04 over 11.10 on an old laptop 

(see this bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/875343](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/875343))

I tried adapting one of the suggested workaround and renamed my /var directory as "oldvar". This has worked and the installation is now proceeding on the laptop. But I'm curious as to what actually happened when I ran "sudo mv /var oldvar". Once executed, /var seemed to have gone: ls brought up all the other expected directories, but no var. But neither was there any sign of a directory "oldvar". I tried "cd /oldvar" and was told no such file or folder. But when I ran "find oldvar" I got a long list of all the stuff that was previously in var: eg /oldvar/backups/... ; /oldvar/cache/... etc. So the renaming seems to have happened and all the content is still there in the renamed "oldvar", but why can't I see that directory or access it? Hopefully an answer will help me learn a bit more of how linux works.

---

### Post by dino99 on 2012-06-04
the bug you talk about refered to a custom /var, which might not concerned your 11.10 install.
This oldvar can be moved inside your /home or somewhere else, use nautilus "search" to locate it (right click on it and select "properties" to see the exact location.

You can change it back: sudo mv  /oldvar /var

to upgrade from 11.10 :

sudo do-release-upgrade -p

or

gksu gedit /etc/apt/sources.list

and replace "oneiric" by "precise"

then update again.

note: your previous command  "sudo mv /var oldvar"  might be "sudo mv /var /oldvar", explaining your trouble.

---

### Post by Erik1984 on 2012-06-04
Probably oldvar is now in /home/yourname (also written as ~). You forgot a leading slash for oldvar to tell Ubuntu where to place it. If you omit the path of a directory it will assume it must me created in the working directory.

---

### Post by nickdc on 2012-06-04
Found it! Yes, in /home/nick, as you suggested Euroman. Thanks for the help, folks. Another little step ... ;)

---

