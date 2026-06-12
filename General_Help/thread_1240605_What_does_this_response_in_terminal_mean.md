---
title: "What does this response in terminal mean?"
date: 2009-08-14
forum: General Help
---

### Post by 3pinner on 2009-08-14
I type in the following command:

~$  sudo ifdown eth0 && sudo ifup eth0

and get the following output:
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.

What's it telling me?

---

### Post by credobyte on 2009-08-14
Are you on wireless ( wlan0 ) or hard-wired ( eth0 ) ?

---

### Post by soapBAR2 on 2009-08-14
> **3pinner said:**
> I type in the following command:

~$  sudo ifdown eth0 && sudo ifup eth0

and get the following output:
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.

What's it telling me?

It's telling you it doesn't know what eth0 is. Type

```
ifconfig
```

and tell me if you have an entry for eth0. If you do, then your settings are screwy. You could try restarting your kernel's networking module

```
sudo /etc/init.d/networking restart
```

But I wouldn't outside of a last-ditch measure..

---

### Post by 3pinner on 2009-08-14
I have a hardwired network with a router.
eth0 I is my network card.
so how do I get the system to recognize the card, even though it is using it to communicate with you!
Thanks


> **soapBAR2 said:**
> It's telling you it doesn't know what eth0 is. Type

```
ifconfig
```

and tell me if you have an entry for eth0. If you do, then your settings are screwy. You could try restarting your kernel's networking module

```
sudo /etc/init.d/networking restart
```

But I wouldn't outside of a last-ditch measure..

---

### Post by 3pinner on 2009-08-15
Any suggestions on how to fix this?

---

### Post by Iowan on 2009-08-15
Try the **sudo /etc/init.d/networking restart** suggestion.  I have better luck with it than ifdown/ifup. If you're using Network Manager, then NM may need a restart, too.

---

