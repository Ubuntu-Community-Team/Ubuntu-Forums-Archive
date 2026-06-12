---
title: "How to start Transmission from a bash script?"
date: 2012-07-17
forum: General Help
---

### Post by stookin on 2012-07-17
Hi

How do I start Transmission from a bash script?
I tried:

[HTML]service transmission-daemon start

/etc/init.d/transmission-daemon start

and

transmission-gtk -m [/HTML]

Precise Pangolin

---

### Post by greenpeace on 2012-07-17
On my box the following works:

```
/usr/bin/transmission-gtk -m 
```

Frequently you'll find the binaries of these programs in the /usr/bin/ directory and you'll need to call it directly from bash to run it.

If you want to find binaries you can use the **locate** program:

```
locate transmission-gtk
```

---

### Post by stookin on 2012-07-17
> **greenpeace said:**
> On my box the following works:

```
/usr/bin/transmission-gtk -m 
```Frequently you'll find the binaries of these programs in the /usr/bin/ directory and you'll need to call it directly from bash to run it.

If you want to find binaries you can use the **locate** program:

```
locate transmission-gtk
```

Whoa Thanks! It worked!

---

