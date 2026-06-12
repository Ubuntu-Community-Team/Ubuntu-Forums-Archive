---
title: "Read-only file system after enabling/disabling root"
date: 2006-01-29
forum: General Help
---

### Post by benn333 on 2006-01-29
I think I did something pretty stupid, hindsight being 20/20. I could use a hand here...

I briefly enabled and then disabled root access using the instructions available on the Ubuntu wiki - [https://wiki.ubuntu.com/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c](https://wiki.ubuntu.com/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c)

Now I'm getting various errors saying my system is now a "read-only file system." (At first I noticed that I couldn't run sudo, then Amorak, then Firefox...) I've rebooted the system and it boots to this point:

```

* Checking root file system...
/ contains a file system with errors, check forced.
/:
Inodes that were part of a corrupted orphan linked list found.
/: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)

* fsck failed. Please repair manually and reboot. Please note 
* that the root file system is currently mounted read-only. To
* remount it read-write:

*    # mount -n -o remount,rw /
* CONTROL-D will exit from this shell and REBOOT the system.

Give root password for maintenance
(or type Control-D to continue): 
```

Neither my user nor the root password I briefly enabled allow me to log in. (Seems an easy enough fix if I could.) 

Can anyone help me get this system going again? Thanks in advance.

---

### Post by benn333 on 2006-01-29
I should mention I enabled root while attempting to install the Doom3 port. It seems that the install requests your root password to proceed. I figured doing so briefly would be harmless enough...

---

