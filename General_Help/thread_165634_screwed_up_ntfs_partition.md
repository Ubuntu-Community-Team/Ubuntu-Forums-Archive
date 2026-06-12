---
title: "screwed up ntfs partition"
date: 2006-04-24
forum: General Help
---

### Post by cosmoshell on 2006-04-24
awhile back i used partition magic to resize the ntfs partition and then when i rebooted windows started to reboot after that ugly logo apeard for 5 secs. also ubuntu did something similer. well a while back somehow i got ubuntu to run but windows still has problems also every time ubuntu boots up it takes for ever to boot becouase its checking the bad file system. keeps saying bad superblock. how can i fix the ntfs partition witout formatting it or at least disable the checkfs thing thats forced.

thanks for any help.

---

### Post by mjziegle on 2006-04-24
remove the line in your /etc/fstab file containing the nt partition.  That should take care of the file system check.

Does windows boot?  You could try the windows recovery console or reinstall  XP on top of the old partition or use the repair option.  You might have to reinstall grub. 

You haven't provided a very good explanation of your symptoms to elicit a quality response.

-Matt

[QUOTE=cosmoshell]awhile back i used partition magic to resize the ntfs partition and then when i rebooted windows started to reboot after that ugly logo apeard for 5 secs. also ubuntu did something similer. well a while back somehow i got ubuntu to run but windows still has problems also every time ubuntu boots up it takes for ever to boot becouase its checking the bad file system. keeps saying bad superblock. how can i fix the ntfs partition witout formatting it or at least disable the checkfs thing thats forced.

thanks for any help.[/QUOTE]

---

### Post by cosmoshell on 2006-04-24
ive already removed it from the fstab" for some strange reason it still does the check. i realy dont think its grub becouase windows starts to boot up just after a few seconds of the windows logo it reboots. same goes when i choose last good settings that worked from the windows menu.

---

### Post by mjziegle on 2006-04-24
Sounds like your windows is hosed.  Gonna have to reinstall.

---

### Post by cosmoshell on 2006-04-24
how can i disable checkfs on initng or the normal booter

---

