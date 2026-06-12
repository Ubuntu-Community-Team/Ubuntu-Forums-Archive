---
title: "slow shutdown"
date: 2010-02-10
forum: General Help
---

### Post by nerdy_kid on 2010-02-10
hi all, my pc takes a long time to shutdown, as it shuts down it displays

Init: statd main process killed respawning

or something very similar and it repeats the process several times over.  This causes the shutdown to lag by about 7 seconds.

any ideas?
 between this and my continual X issues [http://ubuntuforums.org/showthread.php?p=8802157#post8802157](http://ubuntuforums.org/showthread.php?p=8802157#post8802157)
i am starting to get irratated! LOL

---

### Post by nerdy_kid on 2010-02-11
bump

---

### Post by philinux on 2010-02-11
> **nerdy_kid said:**
> bump

Sounds like the shutdown problem is related to your x problem.

What you got in System>admin>hardware drivers

Is the recommended driver for you gfx card in use and activated?

---

### Post by nerdy_kid on 2010-02-11
> **philinux said:**
> Sounds like the shutdown problem is related to your x problem.

What you got in System>admin>hardware drivers

Is the recommended driver for you gfx card in use and activated?

how would it be related to the gfx card?
I am using the 190.53 drivers.

---

### Post by philinux on 2010-02-11
> **nerdy_kid said:**
> how would it be related to the gfx card?
I am using the 190.53 drivers.

X trying to shutdown but with errors I'm guessing.

Try this. Open a terminal.

```
sudo shutdown -h now
```

Also have a look in /var/log/messages see if any clues there.

[edit] looks like this bug. Not X related then.
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/499956](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/499956)

---

### Post by nerdy_kid on 2010-02-11
thanks for that link, should be very useful :)  i probably should learn to search launchpad before posting :S

---

