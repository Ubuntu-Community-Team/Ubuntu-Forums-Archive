---
title: "Add service script to runlevel 5"
date: 2010-09-26
forum: General Help
---

### Post by Telémakhos on 2010-09-26
Hi, 

I'm configuring a VPN and I need to add **[this script]("http://pastebin.com/rtBXhg5u")** to runlevel 5. In the HowTo I'm using it's written that I've just have to download it and execute this:

```
sudo chmod +x ./bridge; sudo update-rc.d ./bridge defaults
```

Should I place it in /etc/init.d renamed as "bridge" and execute that command? I've read that "defaults" will ad the script to runlevels 2-5.  Do I need to do anything else to just add it in the 5 runlevel?

Thanks.

---

### Post by Telémakhos on 2010-09-26
Anyone knows this?

---

### Post by btindie on 2010-09-26
I think the HowTo you've been reading is for a RedHat/openSUSE system as Ubuntu doesn't use [runlevel]("http://en.wikipedia.org/wiki/Runlevel") 5. When it's operation it's in runlevel 2, on other distributions runlevel 5 is multiuser+X11. I'm not sure how well that will fit in with Ubuntu's method of controlling things...
 
Take a look at the following for an alternative way of achieving the same:
 
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging)

---

