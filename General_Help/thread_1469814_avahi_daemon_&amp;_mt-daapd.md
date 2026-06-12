---
title: "avahi daemon &amp; mt-daapd"
date: 2010-05-02
forum: General Help
---

### Post by mashedbear on 2010-05-02
I use mt-daapd music server to stream music to a couple of network music players (which use UPnP protocols). Recently (last month or so) I have found that on restarting my ubuntu system I need to manually restart the avahi-daemon in order for the music players to be able to 'see' the music server. 

I think avahi-damon is running when ubuntu first starts up. The output of a ps aux shows:
> ~$ ps aux | grep avahi
avahi     1005  0.0  0.0  31892  1684 ?        Ss   16:49   0:00 avahi-daemon: running [gandalf.local]
avahi     1006  0.0  0.0  31760   552 ?        Ss   16:49   0:00 avahi-daemon: chroot helper
paul      2816  0.0  0.0   8400   876 pts/1    R+   16:57   0:00 grep avahi

The command I use to restart avahi-daemon is
```
sudo service avahi-daemon restart
``` 

After restarting avahi-daemon mt-daapd server & network music players work just fine. The output from a ps after restarting the avahi service is:
> ps aux | grep avahi
avahi     2890  0.1  0.0  31888  1672 ?        Ss   17:05   0:00 avahi-daemon: running [gandalf.local]
avahi     2891  0.0  0.0  31760   552 ?        Ss   17:05   0:00 avahi-daemon: chroot helper
paul      2893  0.0  0.0   8400   876 pts/1    R+   17:05   0:00 grep avahi

I'd like to understand why I need to restart the avahi-daemon and either solve this or learn a way to automate restarting it on system boot up so I don't have to do it manually each time.

My system is ubuntu 9.10 64 bit and the version of avahi-daemon is 0.6.25

Thanks for any help

---

### Post by fr33loder on 2010-06-20
Hi!

I am having a vaguely similar issue...

How did you solve this one?

thx

---

### Post by ad_267 on 2010-06-20
I had problems with mt-daapd and found forked-daapd works a lot better. See [http://ubuntuforums.org/showthread.php?t=1354196](http://ubuntuforums.org/showthread.php?t=1354196)

It looks like there are Debian packages for 64 bit that should work on Ubuntu, but 32 bit users will have to compile it which can be a bit tricky.

---

