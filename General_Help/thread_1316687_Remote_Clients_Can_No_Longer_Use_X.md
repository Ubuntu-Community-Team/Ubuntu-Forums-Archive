---
title: "Remote Clients Can No Longer Use X"
date: 2009-11-06
forum: General Help
---

### Post by subuta on 2009-11-06
Hello,

I haven't been able to find this problem in any other thread, although [http://ubuntuforums.org/showthread.php?t=1315671&highlight=can't+open+display](http://ubuntuforums.org/showthread.php?t=1315671&highlight=can't+open+display) was enticingly close.

I run 64 bit Ubuntu server with vmware server.  Since I upgraded to 9.10 a couple of days ago and the new vmware server yesterday, my virtual machines are no longer able to open xterms on my physical host (scapps1).  My procedure was to use xhost on my physical host to allow access to the VMs.  I still do that and it seems to complete ok but when I try to run xterms from the VMs they say "can't open display: scapps1:0.0".

I suspect that the problem may be that the upgrade has stopped X from listening to port 6000 for TCP connections.  This is just a hunch based on posts I have found while looking for a solution and on the (empty) output from:

sudo  netstat -plant | grep 6000 

so I am far from certain that this is the issue.  Anyway, I tried telling X to listen for TCP connections a couple of different ways


 - by editing gdm.conf.dpkg-dist
 - by editing /etc/X11/xinit/xserverrc

but so far no luck.

Can anyone confirm that the upgrade to 9.10 could have caused this problem, and/or offer a solution?

I should mention that I am fairly befuddled by X configuration.

Many thanks.

-Dan

---

### Post by monkeygumbo on 2009-12-03
Add these two lines to /etc/gdm/custom.conf.

[security]
DisallowTCP=false
 
Reboot the system and use xhost to allow access.

---

### Post by subuta on 2009-12-04
Thanks, moknkeygumbo.  That is the solution which I stumbled upn a week or so ago.  I also found that I could make X forwarding over SSH work after I made those changes.

---

