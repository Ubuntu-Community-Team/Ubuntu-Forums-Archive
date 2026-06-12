---
title: "rkhunter question"
date: 2010-04-23
forum: General Help
---

### Post by aCsbD6N5xj on 2010-04-23
Hi.

So I did a virus/rootkit scan with rkhunter and nothing was found until at the end of the test where it said:

```
  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
```So I went to the log file and here is what I found at the end of the file:
```

[00:06:41] Info: Starting test name 'filesystem'
[00:06:41] Info: SCAN_MODE_DEV set to 'THOROUGH'
[00:06:41]   Checking /dev for suspicious file types         [ Warning ]
[00:06:41] Warning: Suspicious file types found in /dev:
[00:06:41]          /dev/shm/pulse-shm-3582354715: data
[00:06:41]          /dev/shm/pulse-shm-3521027235: data
[00:06:41]          /dev/shm/pulse-shm-869376325: data
[00:06:41]          /dev/shm/pulse-shm-1148081313: data
[00:06:41]          /dev/shm/pulse-shm-638363505: AmigaOS bitmap font
[00:06:41]          /dev/shm/pulse-shm-999774341: data
[00:06:41]          /dev/shm/pulse-shm-4164775569: data
[00:06:42]   Checking for hidden files and directories       [ Warning ]
[00:06:42] Warning: Hidden directory found: /etc/.java
[00:06:42] Warning: Hidden directory found: /dev/.udev
[00:06:42] Warning: Hidden directory found: /dev/.initramfs

```I'm using ubuntu 10.04 beta btw

Can anyone clarify this for me plz?

Thx

EDIT: I just did another scan with chkrootkit this time and I had this line which is kinda worrying me now coz I didn't get it yesterday when I installed it and did my first scan:

```
Checking `lkm'...                                           You have     1 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed 
```

---

