---
title: "Google chrome crashes on launch"
date: 2011-12-01
forum: General Help
---

### Post by ledererster on 2011-12-01
Google Chrome version Google Chrome 15.0.874.121
Operating System: Ubuntu 11.10
Error Message: When runing from the terminal I get this :


```

justin@Justin:~$ google-chrome
[7563:7577:665603268:ERROR:shared_memory_posix.cc(172)] Creating shared memory in /dev/shm/.com.google.Chrome.x15uo5 failed: Read-only file system
[7563:7577:665603432:ERROR:shared_memory_posix.cc(175)] Unable to access(W_OK|X_OK) /dev/shm: Read-only file system
[7563:7577:665603459:FATAL:shared_memory_posix.cc(177)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.
--2011-12-01 18:13:02--  https://clients2.google.com/cr/report
Resolving clients2.google.com... 74.125.227.75, 74.125.227.78, 74.125.227.67, ...
Connecting to clients2.google.com|74.125.227.75|:443... connected.
[7563:7563:665899120:ERROR:shared_memory_posix.cc(172)] Creating shared memory in /dev/shm/.com.google.Chrome.DOXoOu failed: Read-only file system
[7563:7563:665900062:ERROR:shared_memory_posix.cc(175)] Unable to access(W_OK|X_OK) /dev/shm: Read-only file system
[7563:7563:665901076:FATAL:shared_memory_posix.cc(177)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [ <=>                                   ] 16          --.-K/s   in 0s     


Crash dump id: 61e0a138625ff339
2011-12-01 18:13:03 (495 KB/s) - `/dev/fd/3' saved [16]

Aborted

```

i tried sudo chmod 1777 /dev/shm like it suggests but it was no help. Any suggestions?

---

### Post by Raweed on 2011-12-01
try deleting ~/.config/chromium from the terminal

---

### Post by ledererster on 2011-12-02
It works now. All i did was reboot. I guess it could have been that I originally booted into recovery mood and then chose continue with normal boot. But after a reboot everything works fine. sorry for the inconvenience.

---

