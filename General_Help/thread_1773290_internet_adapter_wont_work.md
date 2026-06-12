---
title: "internet adapter wont work"
date: 2011-06-01
forum: General Help
---

### Post by dukee152 on 2011-06-01
I use a cisco internet adapter to get internet on my computer I recently installed ubuntu as a dual boot and I am typing this message on my windows boot. I would like to use the internet on ubuntu but however the driver won't install on Ubuntu am using a linksys wusb54gsc version 2  if anyone has the same problem or the same internet adapter please holla on the post.

---

### Post by spcwingo on 2011-06-01
With the device plugged in, what is the terminal output of this command (copy and paste in your next post):

```
lsusb
```

If you can't access the internet from Ubuntu at all you can slightly modify the above command to output to a text file instead, like so:

```
lsusb > output.txt
```

This will create a text file with the name "output.txt" in your home folder which can be copied to a flash drive (or directly to you Win partition).

---

### Post by dukee152 on 2011-06-02
Bus 001 Device 003: ID 1737:0075 Linksys WUSB54GSC v2 802.11g Adapter

---

### Post by spcwingo on 2011-06-02
This seemed to work for some users of this adapter:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb54gsc-on-ubuntu-8-04-1-solved-664463/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb54gsc-on-ubuntu-8-04-1-solved-664463/")

Hopefully, it will work for you too.  [-o<

---

### Post by dukee152 on 2011-06-04
> **spcwingo said:**
> This seemed to work for some users of this adapter:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb54gsc-on-ubuntu-8-04-1-solved-664463/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb54gsc-on-ubuntu-8-04-1-solved-664463/")

Hopefully, it will work for you too.  [-o<

It wont work because it is not for version 2 which is the adapter I have

---

