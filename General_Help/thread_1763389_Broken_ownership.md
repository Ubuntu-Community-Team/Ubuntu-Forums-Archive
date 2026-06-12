---
title: "Broken ownership"
date: 2011-05-20
forum: General Help
---

### Post by Howy on 2011-05-20
I've used VirtualBox in the past, and I have lots of virtual machines. However, Natty broke support for 3.2, so I tried 4.0. But 4.0 doesn't work due to the VERR_SUPLIG_OWNER_NOT_ROOT error.
So i tried fixing it with setting ownership and group of /usr to root:root, recursively. (chown -R root:root /usr)
However, now I can't use Software Center or sudo. Gksu crashes. The only way to use root is now su.
Anyone know how I can reset the ownership of the folders and files in /usr?
I want it to be back to normal. :(
And for the record, I've got a backup which includes /usr. But I can't use it because it's too old. (I think it's from before Natty.)
However the permissions are in order for that backup. (Rsync'd through BackInTime)
Thanks in advance.

And another note, most apps work except for those dependant on sudo and gksu. Everything else works fine.

---

### Post by oregonbob on 2011-05-26
I have the exact same problem. My problem started when I upgraded VirtualBox to 4.0.8. None of my VM's run and I get errors like screenshot attached.

---

### Post by oregonbob on 2011-05-26
I solved this in my case it was folder ownership. I did a chown 'root:root /usr/lib' and that solved it for me. Don't do that command recursive if you try it.

---

