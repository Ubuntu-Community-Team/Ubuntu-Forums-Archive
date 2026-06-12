---
title: "Network manager only appears for first user"
date: 2011-06-27
forum: General Help
---

### Post by Martin_sensei on 2011-06-27
Hello,

I am trying to work out if the network manager (the icon in the top right) can be enabled for all users logged on, not just the first.

Sometimes my router drops the connection and it is nescesary to click OK to the password re-entry prompt, however if I have logged on, then someone else is using the system and this happens, I need to log back on, press OK, log back out then let them log back in again.  

Can't the network icon be enabled for all users?

Cheers,

Martin

---

### Post by plucky on 2011-06-27
> **Martin_sensei said:**
> Hello,

I am trying to work out if the network manager (the icon in the top right) can be enabled for all users logged on, not just the first.

Sometimes my router drops the connection and it is nescesary to click OK to the password re-entry prompt, however if I have logged on, then someone else is using the system and this happens, I need to log back on, press OK, log back out then let them log back in again.  

Can't the network icon be enabled for all users?

Cheers,

Martin


Have you tried ticking the box "Available to all users" under "Network Connections"?

---

### Post by Martin_sensei on 2011-06-27
Yes, I have tried this, it makes no difference.  The whole network applet is unavailable for the second person to log on.

---

### Post by Martin_sensei on 2011-06-29
Anyone got any ideas?  I want the whole network management icon to be available for all users...

---

### Post by grahammechanical on 2011-06-29
If you tick the box Connect Automatically you should not need to authenticate the connection. So, with Available to all users checked the next thing to look at is the user privileges in Users and Groups. Does this second user have the privilege of accessing wired and wireless networks?

Network manager stores your password and the wireless pass phrase. That is why you can click OK to get network manager to re-connect. It would be a breach of security to give the second user access to a simple OK click unless you had given this user the privilege to do so.

This is my thinking on the matter.

Regards.

---

### Post by Martin_sensei on 2011-07-08
Connect automatically is checked, all users have permission to access the networks, the connections are set to "available to all users"  however,

If I log on, then a other user logs on, the 2nd user can not even access the networks applet to make a new connection.

I don't care if my user gets a prompt to reconnect, I just want any other use to be able to establish their own connection. Otherwise I have to tell the other user my password (if I'm not home) so they can log in, connect, then log back in as them again.

Surely this is possible...

---

### Post by Martin_sensei on 2011-07-26
Any ideas? Got stuck again this morning, when another user had logged on first and the network disconnected, I had to reboot the machine to gain access to the network manager again...

---

### Post by Wayne_V on 2011-07-26
Is this the issue you are talking about?

[http://blog.jacobodevera.com/2009/07/30/gnome-network-manager-applet-with-multiple-users.html](http://blog.jacobodevera.com/2009/07/30/gnome-network-manager-applet-with-multiple-users.html)

---

