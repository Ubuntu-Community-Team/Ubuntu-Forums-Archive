---
title: "Network manager rescan timeout"
date: 2010-03-08
forum: General Help
---

### Post by moshe88 on 2010-03-08
I'm having a problem with Ubuntu 9.1 network manager. When I disconnect the router and connection to my SSID is lost the network manager will automatically rescan broadcasting networks and try to reconnect. However, if i hold my router off for a certain period of time (more then 2 minutes), the network manager won't connect to my wireless network automatically any more. I have to do it manually all the time.

It seems like there is a timeout for the "Rescan". I would guess that if the network manager does not find any familiar networks for 2 minutes it won't start looking unless you activate the search manually.

I'm looking for suggestions to either change the time out option (if there is anything like that) or write a batch command that will be running in a loop in the background that will activate the search consistently.


All suggestions welcome.

Thank you

---

### Post by dcstar on 2010-03-09
> **moshe88 said:**
> I'm having a problem with Ubuntu 9.1 network manager. When I disconnect the router and connection to my SSID is lost the network manager will automatically rescan broadcasting networks and try to reconnect. However, if i hold my router off for a certain period of time (more then 2 minutes), the network manager won't connect to my wireless network automatically any more. I have to do it manually all the time.

It seems like there is a timeout for the "Rescan". I would guess that if the network manager does not find any familiar networks for 2 minutes it won't start looking unless you activate the search manually.

I'm looking for suggestions to either change the time out option (if there is anything like that) or write a batch command that will be running in a loop in the background that will activate the search consistently.


All suggestions welcome.

Thank you

[http://brainstorm.ubuntu.com/idea/21095/](http://brainstorm.ubuntu.com/idea/21095/)

Also:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394)

---

