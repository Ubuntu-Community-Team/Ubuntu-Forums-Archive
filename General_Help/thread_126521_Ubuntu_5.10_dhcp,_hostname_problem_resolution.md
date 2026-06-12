---
title: "Ubuntu 5.10 dhcp, hostname problem resolution"
date: 2006-02-06
forum: General Help
---

### Post by simpsonb on 2006-02-06
Hi
We have been having fits with getting 5.10 to behave in a dhcp environment.  Regardless of what you did during or after install 5.10 insisted on keeping the host name assigned by dhcp. (dhcp**********.emporia.edu).:( We want to use ubuntu as a server box but who wants to hit a server with a name like that!  Looking at some other posts in the forums indicate that others have been  having this problem.  

Here is the solution.  Edit the file /etc/dhcp3/dhclient.conf as root.  In the line starting request subnet-mask, broadcast-address ... host-name ... netbios-scope; Delete host-name.  Now make a new line after netbios-scope;.  Add the following: 
send host-name "yourhostname";

Save it.

Now restart.  This did it for us.:mrgreen:

---

