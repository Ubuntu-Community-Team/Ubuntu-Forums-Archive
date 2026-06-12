---
title: "/etc/network/interfaces"
date: 2012-02-18
forum: General Help
---

### Post by imaidiot on 2012-02-18
Every time I try to assign a static IP on Ubuntu Server 11 with the command "/etc/network/interfaces"  I get a message "Permission Denied"  

I am the only user, and I just installed Ubuntu Server for the first time.  I have logged on as the "sudo su" with the correct password.  What am I doing wrong?:confused::confused::confused::confused::confused:

---

### Post by Manyette on 2012-02-18
Not sure where you're going here, but are you trying to edit that file? If so, you would have to use "gedit /etc/network/interfaces", or some other suitable editor, perhaps nano. And since it is a system file, you would have to precede the editor commmand with "sudo". I would do that rather than got to "sudo su", which leaves you in supervisor mode.

---

