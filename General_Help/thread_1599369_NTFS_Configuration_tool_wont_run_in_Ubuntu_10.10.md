---
title: "NTFS Configuration tool wont run in Ubuntu 10.10"
date: 2010-10-17
forum: General Help
---

### Post by lechip on 2010-10-17
So i've isntalled Ubuntu 10.10 from fresh.
I do dual run with Windows and i like to share the folder with Win, so i need ntfs-config tool to automount the Win-Data partition.
Installed ntfs-configuration tool and wont launch, tryed through console and got:
> Traceback (most recent call last):  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'

Help!:(

---

### Post by mfhall on 2010-10-17
I have the identical problem - fresh install of 10.10, same error message

---

### Post by bruno9779 on 2010-10-17
In case it helps, on 10.10 upgraded, I have a /etc/hal/fdi/policy/.

---

### Post by ssaint04 on 2010-10-18
I'm using a fresh install of 10.10 x64. ntfs-config won't load for me either. Same error message as the OP.

---

### Post by brunnux on 2010-10-18
I am having the exact same problem. Tried to google if for days and nothing.
And my bigger problem is even when I try to edit my "/etc/fstab" file it works, but my HD names keep changing. Some time my first disc is sda, some times it's sdb, it causes some problems mounting the disk on startup sometimes.
The only thing that used to work was ntfs-config.
(Sorry for bad English.)

---

### Post by brunnux on 2010-10-18
Hey I found a temporary fix. 

Just create this directory on terminal: sudo mkdir -p /etc/hal/fdi/policy
and re run ntfs-config.

---

### Post by Nabor_ on 2010-10-22
I fixed it installing HAL
```
sudo apt-get install hal
```

---

### Post by atulkakrana on 2010-10-23
> **brunnux said:**
> Hey I found a temporary fix. 

Just create this directory on terminal: sudo mkdir -p /etc/hal/fdi/policy
and re run ntfs-config.


It works....Thanks

---

### Post by stead21 on 2010-10-24
> **Nabor_ said:**
> I fixed it installing HAL
```
sudo apt-get install hal
```

Confirmed, 

This works, just ran the following below:

- sudo apt-get install hal

- re-install NTFS Configuration tool

---

### Post by apocolpse on 2010-11-08
This worked for me too 
> **Nabor_ said:**
> I fixed it installing HAL
```
sudo apt-get install hal
```

---

### Post by sougatain on 2011-01-05
> **Nabor_ said:**
> I fixed it installing HAL
```
sudo apt-get install hal
```
It really works. Thank you.

---

### Post by -Strider- on 2011-01-22
> **brunnux said:**
> Hey I found a temporary fix. 

Just create this directory on terminal: sudo mkdir -p /etc/hal/fdi/policy
and re run ntfs-config.

[COLOR="DarkOrange"]Thanx mate. It really worked :)[/COLOR]

---

### Post by balta on 2011-02-03
Installing hal totally did the trick on my new fresh 10.10 x64 install!
Thanks!
However I'm quite confused ... what the hell is 'HAL' and why it was not installed?! (never had such issues using ntfs-config on any fresh x32 install of ubuntu I made)
If anyone does know the answer, I'd be glad to hear it!
Thanks again!

---

### Post by matt-fender on 2011-02-12
Thanks also sorted here on bunty and mint :D

---

