---
title: "why is &quot;aptitude&quot; sometimes used instead of &quot;apt-get&quot; on the web?"
date: 2011-07-10
forum: General Help
---

### Post by nrundy on 2011-07-10
I saw this the other day on ubuntu geek:  sudo aptitude install ddclient

normally I see installs like this: sudo apt-get install "app here"

Does aptitude do same thing as apt-get?

---

### Post by bodhi.zazen on 2011-07-10
> **nrundy said:**
> I saw this the other day on ubuntu geek:  sudo aptitude install ddclient

normally I see installs like this: sudo apt-get install "app here"

Does aptitude do same thing as apt-get?

apt-get and aptitude are both front ends for apt, so they essentially do the same thing, but there are some differences and variations in options and configuration.

See

man apt-get
man aptitude

[http://wiki.debian.org/Apt](http://wiki.debian.org/Apt)

---

### Post by JRV on 2011-07-10
They are mostly the same.

When doing testing on pre-release versions Update Manager will often offer a partial upgrade.  A partial upgrade will usually remove something you need.  In this case I use aptitude to do a safe upgrade with the command:```
sudo aptitude safe-upgrade
```
For everything else I use apt-get.

---

