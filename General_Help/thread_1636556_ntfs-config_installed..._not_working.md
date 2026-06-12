---
title: "ntfs-config installed... not working"
date: 2010-12-03
forum: General Help
---

### Post by madmax.santana on 2010-12-03
I installed ntfs-config like I do every time I install Ubuntu.
But when I click on System -> Administration -> NTFS Configuration Tool, it demands my password and does nothing. So I decided to run it in a terminal to find out what the problem is. So I typed
```
sudo ntfs-config
```
in a terminal, and this came up
```
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'
```

---

### Post by madmax.santana on 2010-12-06
?

---

### Post by Kylotan on 2010-12-09
I had exactly the same problem. I Googled just now and found this:

[https://bugs.launchpad.net/ntfs-config/+bug/630348](https://bugs.launchpad.net/ntfs-config/+bug/630348)

Someone's checked in a fix but obviously it's not come through the package system yet.

I can confirm that making the /etc/hal/fdi directory fixed it for me and allowed ntfs-config to start up properly.

It does still throw exceptions when reading the configuration though, meaning the 'Ok' button doesn't seem to work well. Not the best software I've used recently. (I think that's this bug: [https://bugs.launchpad.net/ntfs-config/+bug/683524](https://bugs.launchpad.net/ntfs-config/+bug/683524))

---

### Post by madmax.santana on 2010-12-10
> **Kylotan said:**
> 

I can confirm that making the /etc/hal/fdi directory fixed it for me and allowed ntfs-config to start up properly.



Thanks a lot bro. It worked. :)

---

