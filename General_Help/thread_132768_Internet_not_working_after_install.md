---
title: "Internet not working after install"
date: 2006-02-18
forum: General Help
---

### Post by Albi on 2006-02-18
Hello, I'm a total Linux newbie, and I upgraded to Ubuntu from Windows XP.  However, the internet connection does not seem to be working, and I have no clue where to go to diagnose the problem.  All I know is that my router, Zonet ZSR0104CP is set up properly as it works with this computer.  It is not a wireless connection, and Ubuntu can connect to 192.168.1.1 to configure the router, but cannot connect to the internet, nor ping anything outside the network, even when the IP address is entered instead of the web page.  I would greatly appreciate some help, I'm very frustrated and have no clue where to begin.

---

### Post by Albi on 2006-02-18
Also, I'm not sure if my Ubuntu is properly networked with this machine.  It doesn't seem to show up anywhere under network neighbourhood.

---

### Post by nanotube on 2006-02-19
i am not sure what the problem is with your network config... since you get an ip address and can connect to configure the router, but cannot ping to the outside, it seems the problem is somewhere at the router. or maybe you have a misconfigured firewall on your machine?

as to not showing up in network neighborhood - ubuntu does not do that by default. to make it show up there you have to install samba ...

---

