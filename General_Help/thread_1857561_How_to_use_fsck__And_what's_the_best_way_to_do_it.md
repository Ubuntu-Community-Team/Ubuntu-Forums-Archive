---
title: "How to use fsck?  And what's the best way to do it?"
date: 2011-10-10
forum: General Help
---

### Post by pretty_whistle on 2011-10-10
Since it can't be done when mounted I want to know *how* as well as *the best way* to do it.

---

### Post by garvinrick4 on 2011-10-10
From another install or from a Live CD (install CD using Try Ubuntu)
```
sudo e2fsck /dev/sdxy

```x being drive
y being partition number.

```
sudo fdisk -l
``` (Lower case L)
Will give partition table.

example below:
rick@rick-narwhal:~$ sudo e2fsck /dev/sda5
[sudo] password for rick: 
e2fsck 1.41.14 (22-Dec-2010)
natty_unity: clean, 254735/737280 files, 1973378/2943911 blocks

---

### Post by pretty_whistle on 2011-10-10
> **garvinrick4 said:**
> From another install or from a Live CD (install CD using Try Ubuntu)
```
sudo e2fsck /dev/sdxy

```x being drive
y being partition number.

```
sudo fdisk -l
``` (Lower case L)
Will give partition table.

example below:
rick@rick-narwhal:~$ sudo e2fsck /dev/sda5
[sudo] password for rick: 
e2fsck 1.41.14 (22-Dec-2010)
natty_unity: clean, 254735/737280 files, 1973378/2943911 blocks
I'll give it a try.

---

### Post by pretty_whistle on 2011-10-10
> **garvinrick4 said:**
> From another install or from a Live CD (install CD using Try Ubuntu)
```
sudo e2fsck /dev/sdxy

```x being drive
y being partition number.

```
sudo fdisk -l
``` (Lower case L)
Will give partition table.

example below:
rick@rick-narwhal:~$ sudo e2fsck /dev/sda5
[sudo] password for rick: 
e2fsck 1.41.14 (22-Dec-2010)
natty_unity: clean, 254735/737280 files, 1973378/2943911 blocks

Thanx for the how-to, it worked like a charm. :P

---

### Post by garvinrick4 on 2011-10-10
> Thanx for the how-to, it worked like a charm.
No problem pretty_whistle you enjoy your Ubuntu and have a nice day.

---

### Post by pretty_whistle on 2011-10-10
> **garvinrick4 said:**
> No problem pretty_whistle you enjoy your Ubuntu and have a nice day.

I *always* enjoy my Ubuntu. :guitar:

---

