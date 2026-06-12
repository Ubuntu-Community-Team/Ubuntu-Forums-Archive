---
title: "Upgraded from 9.04 to 9.10, auto eth0 not connecting"
date: 2009-11-01
forum: General Help
---

### Post by mariovs on 2009-11-01
Hey guys,
I have upgraded to Karmic from Jaunty last night and I ran into multiple issues, the most challenging of which is that I cant get online by connecting to auto eth0.

It worked on Jaunty out of the box, all I had to do to connect was to right click the Network Manager icon and then click on Auto eth0, and it would inform me that its connected and I could browse the net, download updates, msn etc

But now after updating from my 64bit Jaunty I do the same operation only now it doesnt seem to connect, its somewhat weird though since I can ping google but when I try to open any website it seems to be stuck in a loop where it tries to load it until after about 20 seconds it just displays the net error.

I have searched far and wide and checked the daemon log and found this line which would seem like its the much spoken about DSL connection bug in the Network Manager:
"NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module"

I opened the launch pad for more info about this bug, I checked out the links that people offered but am not sure how to apply the solution being that I am a new ubuntu user.
The launch pad page:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205)

Also to my dismay the quick fix to jump start the connection via "pppoeconf" doesnt work as it mentions something about not finding a carrier, I do not have the error message infront of me but if it will help any I will check it again and post.

In the Auto eth0 properties over at the Network Manager I Also tried disabling the option apply to all users in the Auto eth0 properties and set the IPv6 option to ignore.

I would appreciate it immensely if any one has any insight into as I am at my wits end.

Thanks!

---

### Post by mariovs on 2009-11-01
Another thing I noticed is that I am getting assigned an ip address from my router, so it would seem like everything should be working, any ideas anyone?

---

### Post by mariovs on 2009-11-02
*Bump*

---

### Post by mariovs on 2009-11-02
I just tried installing two deb packages one for the Network Manager and the other for Network Manager Gnome from here:

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_amd64.deb](http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_amd64.deb)

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091031t155342.d08484c-0ubuntu2~nmt1_amd64.deb](http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091031t155342.d08484c-0ubuntu2~nmt1_amd64.deb)


Still didnt help...:(, also tried unchecking "Apply to all users".

---

