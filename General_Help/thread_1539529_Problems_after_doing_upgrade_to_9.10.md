---
title: "Problems after doing upgrade to 9.10"
date: 2010-07-26
forum: General Help
---

### Post by gbuddy66 on 2010-07-26
I did the upgrade from 9.04 to 9.10. My daighter tried to log in and could not.  She rebooted and this came on the screen "init: unreadahead main process (2774) terminated satus 5 mountall:/proc/self?mountinfo: no such file or directory
montall: root file system isn't mounted
init :  mountall main process (2775)terminated with status 1
general error mounting file systems
a maintenance shell will now be started
CONTROL-D will terminate this shell and re-try.
root@gPC3:~#
This is the screen we are stuck on any help would be greatly appreciated.

---

### Post by uRock on 2010-07-26
Did the grub offer the kernel menu or does it lock up before hand?

---

### Post by gbuddy66 on 2010-07-26
It only goes to that message.

---

### Post by uRock on 2010-07-26
If you boot from a LiveCD does it show the partitions are intact?

---

### Post by gbuddy66 on 2010-07-26
I bought the computer through New egg with Ubuntu 8.04 already loaded.  It has never had windows on it.  Thanks

---

### Post by uRock on 2010-07-26
If you have a LiveCD and can check that the partitions are still in their proper order, then we'll be able to possibly repair grub or at least be able to copy data to an external source, then do a clean install with an added /home partition(if there isn't one there already.)

---

### Post by gbuddy66 on 2010-07-27
I got to the kernel screen.  then to built in command screen and now I am at unmount file systems.

---

### Post by uRock on 2010-07-27
Use the Restore kernel and select the repair packages selection.

---

