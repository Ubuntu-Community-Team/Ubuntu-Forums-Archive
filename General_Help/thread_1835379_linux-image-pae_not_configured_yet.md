---
title: "linux-image-pae not configured yet"
date: 2011-08-29
forum: General Help
---

### Post by Off Shore on 2011-08-29
This seems to be an unusual problem and I am wondering can anyone suggest a solution.
Running a regular update / upgrade command results in the error below.

```

linux-generic-pae depends on linux-image-generic-pae (= 2.6.38.11.26); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):

```Do I have to trawl through configuration scripts to locate the cause?

Possibly it might be a good idea to enumerate my efforts to date.
It seemed to me I might be able to locate a troublesome package by checking through the status file. 
```

gksudo gedit /var/lib/dpkg/status

```
A thorough search of this file, unfortunately, did not reveal the source of my problem. I need to get my thoughts around this one as I believe this status file should have revealed any issues with packages such as missing dependencies.




Many Thanks

---

### Post by Off Shore on 2011-08-30
This one really had me stumped for a while but eventually I realised the solution was quite simple.
Hopefully someone else might learn from my experience.
I made the mistake of assuming there must be a fault with one or more of the installed packages as the terminal was reporting a dependency problem.
With that in mind I checked the status of each package on my machine. that took quite a time as most Ubuntu installs have a large number of packages installed.  
Unfortunately that turned out not to be my problem and I had to put my thinking cap on again.
Had I edited any system files ? Yes enlightenment! I remembered editing the /etc/default/grub in an effort to tame those annoying Plymouth issues we are all plagued with.
There is a bare bones copy of the unedited grub file in /usr/share/grub/default/grub. So, the drill is to open a gksudo Nautilus session and rename the file at /etc/default/grub and then replace it with the unedited version.
Result was ..I am now able to successfully upgrade my installation.
so the moral, boys and girls, is to document any system edits you might make in case you run into problems later on.
Hope this helps someone

---

