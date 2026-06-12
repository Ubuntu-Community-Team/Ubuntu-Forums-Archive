---
title: "Preload - is it running?"
date: 2011-08-12
forum: General Help
---

### Post by woodyg on 2011-08-12
I have installed Preload (0.6.4-1) on Xubuntu 11.04. How do I know if it is running/working? I can't seem to find any reference to Preload in the task manager.

---

### Post by woodyg on 2011-08-15
?

---

### Post by realzippy on 2011-08-15
It runs as daemon.
see:

[http://ubuntuforums.org/showthread.php?t=832429](http://ubuntuforums.org/showthread.php?t=832429)

Btw,when using preload it might be a good idea to lower swappiness also (if you have lots of RAM)...

To check the swappiness value (default=60)

```
cat /proc/sys/vm/swappiness
```

To change the swappiness value temporarely

```
sudo sysctl vm.swappiness=10
```

To make a change permanent, edit the configuration file :

```
gksudo gedit /etc/sysctl.conf
```

Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so:

```
vm.swappiness=10
```

Save the file and reboot. 

Source:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I use swappiness=0 for years without having problems.

---

### Post by woodyg on 2011-08-19
Thanks for the help.

```
sudo tail -f /var/log/preload.log
```gave me lots of

```
[Mon Aug 15 13:00:26 2011] loading conf from /etc/preload.conf
[Mon Aug 15 13:00:26 2011] loading state from /var/lib/preload/preload.state
[Mon Aug 15 13:00:26 2011] failed reading state from /var/lib/preload/preload.state: line 366: invalid syntax
[Mon Aug 15 13:00:26 2011] Exiting
```where the problem seemed to be near empty lines like this


```
MAP    282    10    188416    4096    -1    file:///usr/lib/firefox-5.0/libs
MAP    1052    
MAP    1052    10    4096    4096    -1    file:///usr/lib/pulse-0.9.22/modules/module-x11-publish.so
```in preload.state and tons of 

```
[Mon Aug 15 13:02:38 2011] loading conf from /etc/preload.conf
[Mon Aug 15 13:02:38 2011] loading state from /var/lib/preload/preload.state
[Mon Aug 15 13:02:38 2011] failed reading state from /var/lib/preload/preload.state: line 411: duplicate index
[Mon Aug 15 13:02:38 2011] Exiting
```After reinstalling it all seems to work... for now. Haven't yet seen any quicker loading so may have to wait a bit more.** Do you know how to check how Preload is improving load-times?**


Regarding swappiness... [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?) states that "A value of swappiness=10 is recommended" but says at the same time that "default setting in Ubuntu is swappiness=60" and "Reducing the default value of swappiness will probably improve overall performance for a typical Ubuntu desktop installation". 
Does anyone know why the the default is not set any lower then?

---

### Post by Ron O on 2013-03-26
In case someone stumbles onto this in a search.

I have Ubuntu 12.04- 64 and I was getting all of the nonsense above. But I opened Nautilus as root and found /var/lib/preload/preload.state  and opened it with jedit (gedit might work) and found all kinds of activity- pages full. Also I had timed my boot up time and a few app startup times before installing preload. Boot up took 8 seconds longer (loading the daemon, I guess), but Firefox (for one) now loads twice as fast. Though I did not time it, Amarok seems to be loading WAY faster. So it seems to be working. (Wish I had timed more apps before installing it.)

---

### Post by wildmanne39 on 2013-03-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

