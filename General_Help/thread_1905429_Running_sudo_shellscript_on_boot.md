---
title: "Running sudo shellscript on boot"
date: 2012-01-06
forum: General Help
---

### Post by gameguy on 2012-01-06
I have a broadcom wireless adapter in my laptop, and the drivers for linux don't work for it by default. I tried the sticky on broadcom devices, still didn't work.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
I followed those instructions and got it working fine, except it doesn't start upon boot each time. I need to use the command:
```
sudo insmod ~/.wless/wl.ko
```(yes, I moved the directory to ~/.wless).

So basically, I was looking for a way to either:
a) insert that module permenantly
b) execute that command upon startup

at the moment, I have a shellscript which I put in init.d. The shellscript runs (I tried the command mkdir ~/test and that worked) thanks to rcconf, but the command doesn't actually work. Here is the command I made. The shellscript works fine from a user session, but on startup, it doesn't appear to work.
```

echo "mypassword" | sudo -S insmod ~/.wless/wl.ko

```
But before then, I just want to get it working (or go with method a). I get the feeling the problem is that I'm giving it my sudo password in stdin (-S takes from stdin), which works fine in my user session, but when actually booting, it has a different thing required to do sudo or something like that.

And yes, when I finish I will change the file permissions to 711, and make the owner root (which should be r/w/x for root, x for everyone else)

---

### Post by Basher101 on 2012-01-06
put your script into startup applications and point the command box to your script

p.s. brofist on the i5 2500k overclocked :D

---

### Post by gameguy on 2012-01-06
Works great :D, thanks

PS. What cooler do you run? I'm on a hyper212+. I also build computers for friends, so I like to know what coolers I should buy, even if I'm not in the market for one.

---

