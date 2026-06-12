---
title: "Starting a vpn service company --HELP"
date: 2012-07-24
forum: General Help
---

### Post by nicolasdr on 2012-07-24
hello,
I am trying to set up a paid vpn server (1gbit) and i was thinking of setting it up using ubuntu and openvpn.Is this a good solution?

I want the users to be authenticated by radius(do i need ldap also?).I will provide 3 packages.let's say the free package with a speed limit of 1mbit, a second package with 50gb traffic and speed 6mbit(after the bandwidth limit the speed should fall to 1mbit) and a third package offering 100gb traffic and the same speed restrictions as the second package.

How many servers do i need at first.Can i setup radius on the vpn server?do i need a domain controller?

Furthermore is it possible to create groups,let's say freevpn group,50gb group and 100gb group so as users assigned to groups have the limitations? 

I need a bandwidth monitor and after the limit has reached the user must be assigned to different group.Also when adding servers i need to know how to load balance between servers and use more than one wan ip's.

But one more problem is the billing system.is there a package for billing system?Users will be able to upgrade their package and and the accounts must be created automatically.I know that i need to write some scripts but i have to know the philosophy to start this bussiness.

Thank you in advance guys..I know i am asking many things but i need some help.

PS: Do i need to use pfsense?

---

### Post by nicolasdr on 2012-07-26
No one can help?i used freeradius and daloradius gui for AAA server...What about the openvpn part?is it preferable to use pfsense?

---

