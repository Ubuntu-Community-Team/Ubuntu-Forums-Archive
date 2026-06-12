---
title: "Problems Installing Ubuntu With Windows 7"
date: 2010-05-03
forum: General Help
---

### Post by Vandis on 2010-05-03
I want to install ubuntu on the same partition as windows 7 but when i start to install i do not get the option to install side by side. I'm not sure why. Also I've tried to create 2 partitions one for windows 7 and one for ubuntu but I can't get ubuntu to install. What file system should i use or how on earth can I get that option to install side by side to show up? It just isn't there. Thank you been trying to get this to work so many times. I'm on my 6th windows 7 install today.

---

### Post by zvacet on 2010-05-03
Choose manual way and format Ubutu partition as ext4 mountpoint root /.If you have enough space you create home partition ext4 mountpoint /home.ANd of course you will need swap partition (few GB).Root can be ~10GB and home rest of free space.If you have separate home your files/settings will be safe.

---

### Post by wilee-nilee on 2010-05-03
> **zvacet said:**
> Choose manual way and format Ubutu partition as ext4 mountpoint root /.If you have enough space you create home partition ext4 mountpoint /home.ANd of course you will need swap partition (few GB).Root can be ~10GB and home rest of free space.If you have separate home your files/settings will be safe.

Good advice there are a bunch of wiki information on dual booting, here is a link for a lot of great information.
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)
Others may post more links to get you going as well.

---

