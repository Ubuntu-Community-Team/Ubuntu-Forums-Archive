---
title: "Problems setting up lirc on ubuntu 11.10"
date: 2011-12-10
forum: General Help
---

### Post by fritz222 on 2011-12-10
Hi guys

I installed Lirc on my PC (Ubuntu 11.10 Minimal) according to this tutorial:
[http://ubuntuforums.org/showpost.php?p=11172488&postcount=52](http://ubuntuforums.org/showpost.php?p=11172488&postcount=52)
(I have a moncaso 312)

Everything runs fine till step 8:
I don't have a /etc/init.d/lirc -File and I don't have a  /etc/lirc/hardware.conf -File.
I created them manually and put the stuff in I need according to the tutorial above.

Then I tried to run the following commads and I'm getting these errors:
```

[LIST=1]
[*]xbmc@htpc:~$ irw
[*]connect: No such file or directory
[*]xbmc@htpc:~$ irw /dev/lircd
[*]connect: No such file or directory
[*]xbmc@htpc:/etc/lirc$ sudo irrecord -H mplay2 -d /dev/ttyUSB0 ~/test
[*]sudo: irrecord: command not found
[/LIST]

```I got the same errors when I tried it with:
```
sudo apt-get install lirc
```Also the same problem when I install Lirc Version 0.9.0.

Does anybody have an idea to get it working?
Thank you very much!
Regards

---

