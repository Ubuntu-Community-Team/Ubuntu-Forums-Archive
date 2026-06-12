---
title: "jdb constantly writing to disk"
date: 2011-08-07
forum: General Help
---

### Post by squaregoldfish on 2011-08-07
I've just completed a fresh install on natty, and I'm seeing constant disk writes of around 1Mb every couple of seconds.

I looked at iotop to find the culprit, and it seems to be the journalling manager for the ext4 filesystems:

```
215 be/3 root        0.00 B/s   19.23 K/s  0.00 %  5.89 % [jbd2/sda1-8]
```

Is there something I can do to adjust this behaviour somehow? I'm a bit concerned about wearing the disk out before its time...

Steve.

---

### Post by NightwishFan on 2011-08-07
The process being used is: [https://secure.wikimedia.org/wikipedia/en/wiki/Journaling_block_device](https://secure.wikimedia.org/wikipedia/en/wiki/Journaling_block_device)

I would assume it is normal. Wearing out the device I would only be concerned if you have your disk set to spin down and it spins up all the time. You can check if your disk is set to spin down by running this command: sudo hdparm -B /dev/device

For example:
```
sudo hdparm -B /dev/sda

/dev/sda:
 APM_level      = 254
```

If it reads 254 your disk is on full performance mode and does not permit spindown.


Edit: I should note that my system has this process, but over a time period of 30 seconds it did not do any read/writes as far as I can see. (I am running Debian Testing). So I am not sure if it writing back all the time is normal or not.

---

### Post by squaregoldfish on 2011-08-08
Apparently the APM level is unsupported. However, the load cycle count doesn't seem to be higher than I'd expect, so it's not spinning down/up a lot.

I'll work on the assumption that everything's fine.

Steve.

---

