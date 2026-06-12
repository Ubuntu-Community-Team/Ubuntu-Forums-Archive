---
title: "Ubuntu boot problem"
date: 2012-03-09
forum: General Help
---

### Post by Meijuh on 2012-03-09
Hi,

All of a sudden I have this weird problem with my laptop.

I booted my laptop this morning. It booted through the bios, through grub and then into the ubuntu loading screen with does 5 dots. After about 30 seconds it all of a sudden highlights all the 5 dots and then hangs.

When I select recovery mode in grub I can get to a terminal, but I have no internet connection (at least no DNS), maybe I can ping an IP, haven't tested that yet. wget [http://google.com](http://google.com) does not work. Also I use gnome 3.2 with lightdm. $ sudo service lightdm restart has no effect. It completely hangs, i.e. it shows some log and then won't continue after 'checking battery state'. 'checking battery state' shows [OK]. When I enter $ sudo apt-get autoremove it wants to remove (what I think are) important packages like something as libsound etc. It tries to remove about 50 packages totaling 24MB. I haven't executed this command yet. $ sudo apt-get upgrade does not work, because I have no dns.

It also seems I can not boot from an Ubuntu 11.10 x64 live cd. (So this means it could be a hardware problem).

Currently I am doing a hdd + memory check (build into the bios by HP).

Is there any other way for me to analyze what is going on? Maybe check some log files?

---

### Post by winh8r on 2012-03-09
When you get to the terminal enter:

```
cat /var/log/dmesg | less
```

to see the log and look for anything that looks wrong there.

---

### Post by Meijuh on 2012-03-09
So I managed to get my lan working (I had a static ip configured).

I have a pastebin of cat /var/log/dmsg : [http://pastebin.com/A515WC3H](http://pastebin.com/A515WC3H)

If someone would care to look at this, would really be appreciated, because I don't really understand what it is saying.

FYI, when I do $ sudo service lightdm stop, ubuntu says stop: Unknown instance, so I guess this means lightdm is not running.

---

