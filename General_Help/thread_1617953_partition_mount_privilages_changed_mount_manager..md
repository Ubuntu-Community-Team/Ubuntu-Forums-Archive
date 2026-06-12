---
title: "partition mount privilages changed mount manager."
date: 2010-11-10
forum: General Help
---

### Post by kirkface8 on 2010-11-10
Ive posted to threads before this with the same problem. with nobody having answers i resulted in do a backup and and reinstall. 6 hours later everything was back to normal.
 
5 minutes ago i was using 'mount manager' to try and succesfully mount a seperate partition on startup. Mount manager said all task were sucessfully complete. As i reboot the plymouth loops.
Pushing f1 reveals that ```
the main process (336) terminated with status 1
```
 
i cannot boot at all. Recovery mode hangs with the errors
```
init: mountall main process (422) terminated with status 1

init: failed to spawn mountain post-stop process: unable to exectue: Permission denied
```
 also these processes followed the same structure as above.
spawn plymouth
spawn mountall
spawn mountall-shell
spawn udev 
 
 
I beleive it is mount manager that caused these problems due to chaning the permissions on which user can mount the disks.
 
Can anbody help?
 
lastly if your using ubuntu 10.10 DO NOT USE MOUNT MANAGER.
 
thanks
kirkface8

---

