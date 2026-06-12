---
title: "Ubuntu update froze, now /tmp:waiting for (null)"
date: 2010-04-11
forum: General Help
---

### Post by oake on 2010-04-11
Updating Ubuntu to the next release when it stopped (>6hrs no activity)

In recovery mode it gets to  
         one or more mounts listed in /etc/fstab cannot yet be mounted
         /: waiting for /dev/disk....UUID=4e1797f5-...
         /tmp: waiting for (null)
         swap: waiting for UUID=550c3e90-.....

 and freezes... but escape does bring up a command line shell but what can I do?
  

 Note
 - Been using this dual boot machine in the other mode for several days and no hardware issues
 - LiveCD partition editor can see all partitions and UUID's check out
 - not used an editor on the command line (or could it be done from the live cd?)
 - not found similar issue on forum

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
[This link]("http://ubuntuforums.org/showthread.php?t=1316446") suggests a fix.

---

### Post by oake on 2010-04-11
>>[This link]("http://ubuntuforums.org/showthread.php?t=1316446") suggests a fix.
 to a SWAP space problem not a /tmp (null) problem which the original poster and
myself have
 

 wanted to have a look at my fstab so used the suggested >> sudo gedit /etc/stab
 on the comand line and it retorts ...cannot open display
 

 So  
 as there is no /tmp in gparted can't re-new the UUID and bemused how to edit the fstab if I could?
 

 found the "PC (Intel x86) alternate install CD" and will give that a try when I get it
 onto a CD (I don't have a burner). Anyone know what are the critical options?

---

