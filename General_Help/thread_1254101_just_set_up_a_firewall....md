---
title: "just set up a firewall..."
date: 2009-08-30
forum: General Help
---

### Post by flyingsliverfin on 2009-08-30
i just set up a firewall  cuz i realized i had a ssh server running (forgot) and want to set up a vnc server

however, now when i ssh back to the same computer that im ssh-ing from (which used to work) it says: connection refused
it even says that when i disable the firewall

additional info:
using firestarter

---

### Post by dearingj on 2009-08-31
Are these two computers connecting to each other over the Internet, or a local network? Is either one behind a router or other hardware firewall?

---

### Post by flyingsliverfin on 2009-08-31
actually forget what i said...

i just reinstalled ubuntu and i didnt set up a new ssh server! ](*,)


now that i got that working... the firewall (when active) should NOT let me ssh in from another place... right?

im not a networking person, so, if i want to ssh in from another place that insnt on the local network (which, to answer ur Question, is yes, i am stuck behind a router), how do i need to do this... do i need to memorize my IP and then use it on another computer?

how do i find out if my router is doing dynamic or staitc IP asignment?

---

### Post by JK3mp on 2009-08-31
A router usually assigns ip's dynamically acting as a mini dhcp server, but computers gaining IP's from the router will naturally ask for the same IP if possible though this sometimes this isn't an option(confliction on network, ip taken etc.) and the router has to assign it a new ip of the subnet.

---

