---
title: "/etc/sudoers NOPASSWD not working"
date: 2011-06-25
forum: General Help
---

### Post by fire-fly on 2011-06-25
Hi
visudoers with the following.
> 
#Cmnd alias specification
Cmnd_Alias STORAGE = /sbin/fdisk, /bin/mount, /bin/umount

Cmnd_Alias SOFTWARE = /usr/bin/apt-get

# User privilege specification
root    ALL=(ALL:ALL) ALL
adm   ALL=(ALL) NOPASSWD:   /usr/bin/virsh, /usr/bin/halt, SOFTWARE , STORAGE



However, when login as adm, and execute "sudo apt-get install firefox", it still ask for password.

Please help

Thanks

---

### Post by gmargo on 2011-06-25
It works fine for me.
Did you create an 'adm' user id?

Is that your entire /etc/sudoers file?
I ask since the file is interpreted as "last match wins", so if you have additional lines, they may be applicable.

---

### Post by blueridgedog on 2011-06-25
Below that you may have "%admin ALL=(ALL) ALL" and if adm is in the admin group, you have reset your setting from above.

---

### Post by fire-fly on 2011-06-25
> **blueridgedog said:**
> Below that you may have "%admin ALL=(ALL) ALL" and if adm is in the admin group, you have reset your setting from above.

Hi,
You right, that was the problem.
Thanks!

---

### Post by blueridgedog on 2011-06-26
Well, as gmargo stated, "last match wins", glad you have it sorted.  I advise against sudo ability without a password but respect your right to manage your system as you wish.

---

