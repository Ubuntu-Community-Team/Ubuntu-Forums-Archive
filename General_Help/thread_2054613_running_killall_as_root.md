---
title: "running killall as root"
date: 2012-09-07
forum: General Help
---

### Post by PGScooter on 2012-09-07
I need to run the following command in a script for a workaround:
```
killall NetworkManager
```
However, I get
```

NetworkManager(8515): Operation not permitted
NetworkManager: no process found

```
The following does what I need
```

sudo killall NetworkManager

```
How can I make killall run as sudo killall in the script?
I tried adding the following line to /etc/sudoers with sudo visudo
```

ALL ALL=NOPASSWD: /usr/bin/killall

```

but that did not change anything (I still get the same output as above after restarting).

Any ideas?

Thanks

---

### Post by idoitprone on 2012-09-08
> **PGScooter said:**
> I need to run the following command in a script for a workaround:
```
killall NetworkManager
```However, I get
```

NetworkManager(8515): Operation not permitted
NetworkManager: no process found

```The following does what I need
```

sudo killall NetworkManager

```How can I make killall run as sudo killall in the script?
I tried adding the following line to /etc/sudoers with sudo visudo
```

ALL ALL=NOPASSWD: /usr/bin/killall

```but that did not change anything (I still get the same output as above after restarting).

Any ideas?

Thanks

```
sudo script
```

---

### Post by Primefalcon on 2012-09-08
one word..... don't

---

### Post by raja.genupula on 2012-09-08
+1 to Primefalcon 

this is the reason [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PGScooter on 2012-09-08
ok, thanks for the advice. I thought that was a bad idea, but I couldn't think of anything else.

Do you have any other ideas? I need to kill NetworkManager right after startup (or maybe 20 seconds after).

Thanks.

---

