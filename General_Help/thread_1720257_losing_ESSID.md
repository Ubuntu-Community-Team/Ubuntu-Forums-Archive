---
title: "losing ESSID"
date: 2011-04-03
forum: General Help
---

### Post by moshe88 on 2011-04-03
Hey guys, facing a weird issue - hoping someone might be able to help.

The wireless network on my laptop is configured with a static IP. (not using nm)

When i take the laptop out of the range of my wireless router the essid is becoming off/any therefore when i'm back in range the connection is not reestablished and to re-enable the connection i gotta do "iwconfig wlan0 essid <essid name>"
otherwise there is no connection. 

Anyone knows how to fix that? and make sure that essid stays configured unless i manually want to change it?

---

### Post by dcstar on 2011-04-03
> **moshe88 said:**
> Hey guys, facing a weird issue - hoping someone might be able to help.

The wireless network on my laptop is configured with a static IP. (not using nm)
........

What is wrong with using the Network Manager to set the Static IP?

---

### Post by moshe88 on 2011-04-03
Nop, network manager doesn't work for me. It gives me problems....

anyway to do it without?

---

### Post by jchiar on 2011-04-05
I just looked up the Man page on that, hope it helps.
[http://manpages.ubuntu.com/manpages/intrepid/man8/essidscan.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/essidscan.8.html)
And: 
[http://manpages.ubuntu.com/manpages/intrepid/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/interfaces.5.html)
I am testing them now on a home installation with a wireless device.
I did get one derivative to run or find the DHCP now I am testing it with Debian 6.01a(D_kfreebsd)

---

### Post by tredegar on 2011-04-05
**wicd** works for me.
It is now in the repositories.
Beats network-non-manger hands down, but when I last tested, NM worked better for 3G "mobile phone dongles"

YMMV

---

