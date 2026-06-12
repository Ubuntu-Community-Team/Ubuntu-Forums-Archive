---
title: "Access to LAN Shares stopped after installing Samba"
date: 2010-03-07
forum: General Help
---

### Post by eternallight569 on 2010-03-07
_**PROBLEM:**_

When I first installed Ubuntu, I could access Shares on other Windows machines on the network just fine.  I could not, however, create shares on my Linux machine and was directed to install Samba.

After doing so, I lost all access to my LAN network (however, the Internet works just fine).


[U][B]DETAILS:

[/B][/U]On system startup, I occasionally get the following pop-up message on the upper right corner of my desktop:

[B][I]Network Discovery Service Disabled
[/I][/B]*Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery.  The service has been disabled.*

This is not a regular occurrence, but does happen every once in a while.

What does happen consistently is when I go to Places > Network and attempt to click on the "Windows Network" icon.  I get the following dialog box:

[I][B]Unable to mount location
[/B]Failed to retrieve share list from server[/I]

None of these things happened before installing Samba and I could access network shares just fine.


_**TECH SPECS:**_

I am running Ubuntu Karmic Koala (9.10) on a Compaq Deskpro EN desktop computer.  800 MHz Processor / 512MB RAM, motherboard-based ethernet port.

I am connecting to a router which serves as the Internet gateway as well as the LAN switch for my home network.



The machine networked just fine under my Windows installation, and accessed other shares just fine under Ubuntu.  In order to create shares on Ubuntu, I had to download and install Samba... after which all LAN access died.  The Internet works, though.

Help...?

---

