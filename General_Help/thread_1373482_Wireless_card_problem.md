---
title: "Wireless card problem"
date: 2010-01-05
forum: General Help
---

### Post by InfectedShadow on 2010-01-05
I recently got a Dell Mini 10v and promptly installed Ubuntu on it (Regular, not the netbook remix), and for some reason it doesn't seem to detect the wireless card for the netbook. Any suggestions as to how to make it detect it's there?

---

### Post by spiderbatdad on 2010-01-05
maybe this?
```
cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0

```
[http://en.community.dell.com/forums/t/19288353.aspx](http://en.community.dell.com/forums/t/19288353.aspx)

See this also...probably first thing to try:[http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook](http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook)
Enable the broadcom driver.

---

### Post by InfectedShadow on 2010-01-05
> **spiderbatdad said:**
> maybe this?
```
cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0

```
[http://en.community.dell.com/forums/t/19288353.aspx](http://en.community.dell.com/forums/t/19288353.aspx)

See this also...probably first thing to try:[http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook](http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook)
Enable the broadcom driver.

Tried that. 'No such file or directory'

And I tried the backports but it doesn't find the package.

---

### Post by linux nut on 2010-01-05
you should check if there are any kernels that have the driver installed. I had a similar problem with an eee pc.

---

### Post by spiderbatdad on 2010-01-05
```
sudo apt-get install bcmwl-kernel-source
```
Then System>>Administration>>Hardware drivers. Enable the broadcom driver and reboot. Sorry I thought the link referred to installing this package.

---

### Post by InfectedShadow on 2010-01-05
Turns out part of the problem with the packages not being found was one of the repositories wasn't enabled. Either way now there's a new problem. I got the backports, I got the bcmwl-kernel-source. But when I go to the hardware drivers menu and click activate, enter my password, it doesn't activate. Any idear? :s

---

### Post by linux nut on 2010-01-05
usually it takes along for me for the drivers to activate and a reboot is also necessary

---

### Post by InfectedShadow on 2010-01-05
> **linux nut said:**
> usually it takes along for me for the drivers to activate and a reboot is also necessary

The little window that says "downloading...installing..." literally flashes for 2 seconds and closes. Tried rebooting as well, still have the problem.

---

### Post by linux nut on 2010-01-05
1. try running sudo apt-get update in terminal then try it again.
2. Even though the downloading and installing drives flashes it might still be installing them which is how it happens for me

---

### Post by InfectedShadow on 2010-01-05
> **linux nut said:**
> 1. try running sudo apt-get update in terminal then try it again.
2. Even though the downloading and installing drives flashes it might still be installing them which is how it happens for me

Still no good. Waited 30 minutes since the last activate drivers attempt and still happening. =\

---

