---
title: "Problem with Samba &amp; user"
date: 2009-07-02
forum: General Help
---

### Post by zay2 on 2009-07-02
Hello

I have my samba share set up and its working (almost) fine.

/etc/fstab contains such line:
//192.168.1.66/public /home/mydir/linktoshare smbfs credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777 0 0

Computers connects to share at startup and everything is super.

But there is this strange thing.. when i switch to /home/mydir/linktoshare folder, all those folders/files there do not belong to my user, they do not belong to root user either.. for some strange reason all those files belong to the other user account in this computer (system is kubuntu 9.04)

I have samba share set up in another computer with exactly same way and it works much better. Only difference is that in that computer i am the only user. 

so... how do i set up this samba stuff so i could actually change the shared files (right now iget this annoying red only stuff)

Alan.

---

### Post by zay2 on 2009-07-02
Bump!

---

### Post by zay2 on 2009-07-03
bump

---

