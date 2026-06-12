---
title: "/dev/shm does not exist"
date: 2012-07-25
forum: General Help
---

### Post by KeremE on 2012-07-25
When I tried to open google-chrome, I received the following error: 

[28228:28251:6555757260:ERROR:shared_memory_posix.cc(171)] Creating shared memory in /dev/shm/.com.google.Chrome.x4LJvf failed: No such file or directory
[28228:28251:6555757388:ERROR:shared_memory_posix.cc(174)] Unable to access(W_OK|X_OK) /dev/shm: No such file or directory
[28228:28251:6555757422:FATAL:shared_memory_posix.cc(176)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.


I soon found out that /dev/shm did not exist on my system. I am not sure what's wrong? This happened soon after a system freeze that resulted in me forcing a hard reboot.

Thanks!
KeremE

---

