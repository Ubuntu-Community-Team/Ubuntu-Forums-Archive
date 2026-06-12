---
title: "How to connect two ubuntu computers together to tranfer data through router"
date: 2012-10-13
forum: General Help
---

### Post by JacobTwitch on 2012-10-13
I have quite a few computers with different distros on them.  I have a laptop with Ubuntu 10.10, a desktop with OpenSUSE 12.2 and a gaming PC with Debian Squeeze/Linux Mint 10 (dual boot).  I just installed Ubuntu 12.04.1 on my Moms laptop today and I would like to connect this laptop to some of my other computers to transfer data to it.  I can't use a flash drive because one of my laptops has a problem transfering data through USB and CDs.  What would be the best way to set this up?  Do I need an ethernet cable from one laptop to another or can I do it wirelessly?  I have already tried to set it up and set up permissions on my Ubuntu 10.10 laptop (lets call it Laptop B) so I can have the Ubuntu 12.04.1 laptop (lets call it Laptop A) connect to it.  I also entered the MAC address of laptop B into the network connections on Laptop A.  Laptop B told me that computers can connect to it by using the IP address 10.0.0.7.  When I ping that on Laptop A, I get responses.  Am I doing this right?  If I am what else should I do or what am I missing.  When I click 'browse networks' and open 'Windows networks' (only folder visible) on laptop A it says unable to mount location.  Thanks very much for your time and help!  I am a school student and started using Linux 2 years ago and I am still learning how things work.

---

### Post by steeldriver on 2012-10-13
You probably just need to install the Samba server package on at least one of the machines - either via Software Center / Synaptic, or via command line

```
sudo apt-get install samba
```

---

### Post by JacobTwitch on 2012-10-13
Ok Thanks.  I installed samba by running the command.  But not sure exactly what it is.  is it a command line program or is it a program with a gui?

---

### Post by stinkeye on 2012-10-13
It's fairly simple.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1547389")
What you need is in the third post by ***Morbius1***

---

