---
title: "Can't copy or move to ntfs file system"
date: 2011-12-06
forum: General Help
---

### Post by mkstallings1 on 2011-12-06
Hello.  I have a laptop with two hdds, the first has Windows xp and the second has ubuntu 11.10.  I'm not sure when this started happening, but I can now copy things from my windows hdd to my ubuntu hdd, but not the other way.  I've tried changing permissions on files, but it doesn't matter.  I don't know if this is related, but I tried running "sudo nautilus" and got the following results:


mike@mike-Pavilion-dv8000-EP409UA-ABA:~$ sudo nautilus
[sudo] password for mike: 
** (nautilus:2625): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
[Nautilus Terminal] I: Initializing the Nautilus extension
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

^Cg_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
mike@mike-Pavilion-dv8000-EP409UA-ABA:~$

---

### Post by dabl on 2011-12-06
You don't need samba to mount an internal ntfs partition.

Check this:  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by oldtimer7777 on 2011-12-06
If you have recently done a fresh installation of 11.10 it could be that you need to install:

sudo apt-get install ntfs-3g
> **mkstallings1 said:**
> Hello.  I have a laptop with two hdds, the first has Windows xp and the second has ubuntu 11.10.  I'm not sure when this started happening, but I can now copy things from my windows hdd to my ubuntu hdd, but not the other way.  I've tried changing permissions on files, but it doesn't matter.  I don't know if this is related, but I tried running "sudo nautilus" and got the following results:


mike@mike-Pavilion-dv8000-EP409UA-ABA:~$ sudo nautilus
[sudo] password for mike: 
** (nautilus:2625): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
[Nautilus Terminal] I: Initializing the Nautilus extension
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

^Cg_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
mike@mike-Pavilion-dv8000-EP409UA-ABA:~$

---

### Post by mkstallings1 on 2011-12-06
Thank you very much.  That is exactly what I needed.

---

### Post by oldtimer7777 on 2011-12-06
> **mkstallings1 said:**
> Thank you very much.  That is exactly what I needed.

I thought so... Please make sure to flag this thread as solved. Thank you.

---

