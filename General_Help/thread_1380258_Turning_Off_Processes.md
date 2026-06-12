---
title: "Turning Off Processes"
date: 2010-01-13
forum: General Help
---

### Post by Bezmotivnik on 2010-01-13
I get the following semi-error message and would like to know...

1]  What are the first and last processes in the list, and may I safely turn them off?

2]  How do I do this in command line?

Thanks!

=====================================================
Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
671	avahi-daemon
673	avahi-daemon
674	NetworkManager
759	wpa_supplicant
760	dhclient

---

### Post by cdenley on 2010-01-13
[Avahi]("http://en.wikipedia.org/wiki/Avahi_%28software%29")
[DHCP (dhclient)]("http://en.wikipedia.org/wiki/Dhcp")
```

man update-rc.d

```

---

### Post by Bezmotivnik on 2010-01-13
What's the best command-line set for turning these processes off?

Thanks...

---

### Post by cdenley on 2010-01-14
Well, dhclient shouldn't be started unless you're using DHCP. If you want to prevent it from running, reconfigure your network without DHCP. For avahi, if you're sure you don't want it running:
```

sudo update-rc.d avahi-daemon disable

```

---

### Post by skymera on 2010-01-14
You can disable a lot using sysv-rc-conf.

```
 sudo apt-get install sysv-rc-conf 
```

Be careful with this tool, make sure you know what you are doing!

---

