---
title: "Re-Install"
date: 2006-03-19
forum: General Help
---

### Post by john_markh on 2006-03-19
Is it possible to re-install Ubuntu Breezy ?
I mean, to delete all configurations and packages and leave files ONLY in my home directory.

---

### Post by eyebrowman92 on 2006-03-19
if your home directory is on a separate partition. otherwise, i don't think so.

---

### Post by jerrykenny on 2006-03-19
You can always copy your home directory to a cd using gnomebaker, then when you have made your fresh install, you can copy it back to /home . . . .

when you cut n paste the old home directory . . . say /home/fred

you can then add the "new" user "fred" using the Sys admin users function

and then, issue the command

sudo chown -R fred  /home/fred


make sure you give fred the correct permissions on your system, he needs to be in the "admin" group to use "sudo"  but dont put him in the "sudo" group.

---

