---
title: "Swap help."
date: 2009-11-22
forum: General Help
---

### Post by Ubu4moi on 2009-11-22
How can I make my swap memory work? I have 20gb of swap on a 500gb hard drive and on the System Monitor never shows is active or is being used. I have 4gb of RAM and sometimes the computer gets slow when editing videos but the swap file doesn't seem to activate.

---

### Post by wojox on 2009-11-22
What's your swappiness:

```
cat /proc/sys/vm/swappiness
```

---

### Post by spiderbatdad on 2009-11-22
you can echo a value like:
```
sudo su
echo 100 > /proc/sys/vm/swappiness
```
or you can edit /etc/sysctl.conf for persistence after reboot.

---

### Post by Ubu4moi on 2009-11-22
> **wojox said:**
> What's your swappiness:

```
cat /proc/sys/vm/swappiness
```
It says 60.

---

### Post by Ubu4moi on 2009-11-22
> **spiderbatdad said:**
> you can echo a value like:
```
sudo su
echo 100 > /proc/sys/vm/swappiness
```
or you can edit /etc/sysctl.conf for persistence after reboot.
What's persistance? What will it do?

---

### Post by oldfred on 2009-11-22
You do not want to use swap and 20GB is huge. Swap is using the hard drive which is orders of magnitude slower that RAM menory. Everything I read was when you get over 2GB of RAM swap is rarely used. With lots of memory the only reason the have the same amount of swap as memory was for hibernation. The old rule to 2x memory was when we only had 256k or 512k of memory in the computer.

---

### Post by Ubu4moi on 2009-11-22
So, how much swap should I have? My drive is 500gb.

---

### Post by yester64 on 2009-11-22
> **Ubu4moi said:**
> So, how much swap should I have? My drive is 500gb.

Doesn't matter. If you have over 2GB of ram you most likely don't need swap at all.
I have 1 TB and none and 4GB ram.

---

### Post by Scott753 on 2009-11-22
Yep, previous users are correct. You have enough ram that normal operations don't need to use the swap file. You could set the swap to 0, but if you want to keep some, I would use 4gb as the general recommendation is to have at least as much swap as ram. (But once again, it's probably unnecessary.

The reason your computer slows down during video editing is probably less to do with RAM and more because of your processor/GPU.

---

