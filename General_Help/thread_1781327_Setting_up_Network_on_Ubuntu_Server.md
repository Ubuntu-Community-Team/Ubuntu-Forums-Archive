---
title: "Setting up Network on Ubuntu Server"
date: 2011-06-13
forum: General Help
---

### Post by FerraraZ on 2011-06-13
Hey everyone, firstly I'm a huge newbie with Ubuntu but slowly learning as I go.  I've been following the this guide:

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

To setup a web server at my office (intern).  I'm stuck at updating the web server with the given distro's.  We dont use DHCP and the computer must have static ip address.  I've checked this in /etc/network/interfaces and from what I am seeing, everything is correct (ip address, subnet mask, default gateway, dns servers) however when I go to update I'm still receiving "temporary failure resolving 'us.archive.ubuntu.com etc"

Is there something I am missing or something that I can change or check?  Weird thing is, when I install the ubuntu live disk and have eht0 sets with these values, I can connect to the internet without a problem.

---

### Post by bodhi.zazen on 2011-06-13
Is this problem related to a single site, ie the repos, or can you ping / connect to other sites ?

Also these pages are an alternate source of information:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

