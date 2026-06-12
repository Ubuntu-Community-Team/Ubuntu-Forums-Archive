---
title: "How do I view boot messaes?"
date: 2009-12-16
forum: General Help
---

### Post by Lockheed on 2009-12-16
Where can I find this log? It has nothing to do with dmesg.

---

### Post by mikewhatever on 2009-12-16
I don't think there is a bootlog other then dmesg. You can try and enable bootlogd. cat /etc/default/bootlogd

---

### Post by t0p on 2009-12-16
> **Lockheed said:**
> Where can I find this log? It has nothing to do with dmesg.

Nothing to do with dmesg huh?  That's a tough one.  Umm...

In */var/log* there's a file called *boot*.  But all mine contains is a message: "(nothing has been logged yet)".  Maybe your */var/log/boot* is more useful?

**EDIT:** I just saw mikewhatever's post.

> **mikewhatever said:**
> I don't think there is a bootlog other then dmesg. You can try and enable bootlogd. cat /etc/default/bootlogd

That might be how you get */var/log/boot* to contain something.

---

### Post by Lockheed on 2009-12-16
There are modules loaded at startup I do nto need. These are nvidia 180.... and other stuff (I have 192 installed).
Those messages are nowhere in dmesg and my /var/log/boot says nothing more than "(nothing has been logged yet)".

---

### Post by t0p on 2009-12-16
You need to enable *bootlogd*.  You do this by editing */etc/default/bootlogd* so the last line says

```
BOOTLOGD_ENABLE=Yes
```

Reboot and boot messages should be logged in *var/log/boot*.

---

### Post by vanyinet on 2009-12-16
Maybe /var/log/messages will help you.

---

### Post by Lockheed on 2009-12-16
> **t0p said:**
> You need to enable *bootlogd*.  You do this by editing */etc/default/bootlogd* so the last line says

```
BOOTLOGD_ENABLE=Yes
```

Reboot and boot messages should be logged in *var/log/boot*.

I did that 6 moths ago and it still is empty.


/var/log/messages is just like dmesg

---

### Post by mikewhatever on 2009-12-16
I think you can see what modules are loaded on startup with bootchart. Not quite sure what's wrong with bootlogd.

---

### Post by Lockheed on 2009-12-16
> **mikewhatever said:**
> I think you can see what modules are loaded on startup with bootchart.

Hmmm... How exactly do I use it?

---

### Post by akakingess on 2009-12-16
Try doing the quick search in Synaptic, mine came up with 3 options, bootchart, bootchartgui (or something like that) , and then one other one.

---

### Post by Lockheed on 2009-12-16
I installed it, just have no idea how to use it.

---

### Post by mikewhatever on 2009-12-16
It's been a while since I used bootchart, and then only for a short time, but google is indeed my friend. Hope it still works the same.

[http://onlyubuntu.blogspot.com/2008/07/howto-use-bootchart-to-time-and-track.html](http://onlyubuntu.blogspot.com/2008/07/howto-use-bootchart-to-time-and-track.html)
> Using bootchart may be even easier than installing it... Just reboot! After your machine starts up next time, bootchart will create a graphical representation of the boot sequence (as a .png file), and place it in /var/log/bootchart.

---

### Post by doas777 on 2009-12-16
if your just trying to id modules, wouldn't lsmod be sufficient?

op, it worries me that you are concerned about the specific modules loaded, but you won't google bootchart. perhaps you don't need to worry about the modules at all, and just use your pc.

---

### Post by Lockheed on 2009-12-16
> **mikewhatever said:**
> It's been a while since I used bootchart, and then only for a short time, but google is indeed my friend. Hope it still works the same.

[http://onlyubuntu.blogspot.com/2008/07/howto-use-bootchart-to-time-and-track.html](http://onlyubuntu.blogspot.com/2008/07/howto-use-bootchart-to-time-and-track.html)

Thanks. I got the png image and it seems like potentially very useful but still I see no redundant modules that are being loaded.

---

### Post by mikewhatever on 2009-12-17
> **Lockheed said:**
> Thanks. I got the png image and it seems like potentially very useful but still I see no redundant modules that are being loaded.

Perhaps if you don't see them, they ain't there.

---

