---
title: "URGENT: lost eth1 after update"
date: 2011-10-05
forum: General Help
---

### Post by war.ace on 2011-10-05
I recently added the bt5 repos and I did an update earlier tonight. The update removed quite alot of things and I didnt check what all of them were. Is there any possible way of reversing what I did, reinstall what was removed and get my eth1 back up and running? I think the bt5 repos might have caused it to remove my wireless although I'm not sure.

---

### Post by doas777 on 2011-10-05
here is some info on how to check out what apt/DPKG did during the operation:
[http://ditoinfo.wordpress.com/2007/06/04/apt-get-and-dpkg-log-undo-changes/](http://ditoinfo.wordpress.com/2007/06/04/apt-get-and-dpkg-log-undo-changes/)

see if you can't reverse some of the changes. 

also are you sure you don't have a lan interface anymore?
run ifconfig -a to check. I've had boxes spontaneously change eth1 to eth0 and back again. 
if you have ethtool installed, you can use it to check your interfaces as well, with 
'sudo ethtool eth0' (or eth1, specify your interface).

also check your /etc/network/interfaces file. does it have an "Auto" line and an perhaps an "iface" line for your interface?

---

### Post by war.ace on 2011-10-06
hi doas, thank you so much for your reply, unfortunately too much have been changed to look at the log and pinpoint what change caused my wireless interface to go missing and there is no eth 1 or even eth 0 in my interfaces file

---

