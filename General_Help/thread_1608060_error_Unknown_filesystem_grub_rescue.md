---
title: "error: Unknown filesystem grub rescue"
date: 2010-10-28
forum: General Help
---

### Post by urbanmojo on 2010-10-28
Hello:

I've recently installed Ubuntu 10.10--it had Windows 7 on the machine before but wiped that off so it is not dual boot.

The upgrade manager prompted me to install about 170MB or so of upgrades. I chose to install everything and then rebooted. Upon rebooting I received an error (sorry but didn't record it). I rebooted by ctrl-alt-delete and then got the error:

error: unknown filesystem

grub rescue.

How do I get back my installation?

thx

---

### Post by Quackers on 2010-10-28
Here is a good place to start
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by boot_sectorz on 2010-11-13
I hope you sorted out your problem. In case you didn't, the simplest way I have found (believe I face this problem every other day, not even sure why I installed 10.10 now. I'm total frustrated) is to boot from a livecd (Ubuntu 10.10 or 10.04 can do), and run this code
```
sudo fsck /dev/sda5
```

replace /dev/sda5 with your ubuntu installation partition.
Will ask to fix some errors several times. Click y for 'yes' and after an amount of running code, reboot your system and it will be all good.

I still want to know whats causing this as it really is a loss and a major problem for my work. System just freezes and I have to do this after every other day.

---

### Post by Quackers on 2010-11-13
That sounds like you may possibly have a hard drive failing. I would back everything up, just in case.

---

