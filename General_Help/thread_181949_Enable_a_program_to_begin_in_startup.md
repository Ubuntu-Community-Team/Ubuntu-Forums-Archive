---
title: "Enable a program to begin in startup"
date: 2006-05-25
forum: General Help
---

### Post by stevestyle51 on 2006-05-25
I'm not sure how to go about this in ubuntu.  I need to enable pure-ftpd to begin at startup, I know the command I just need to know where to place it.  The readme seems to not apply to unbutu's system.  Here is the command to start the ftpd
```
/usr/local/sbin/pure-ftpd &
```
It works but I need to make his program begin in the boot sequence.  The readme says to place the above code in the /etc/rc.d/rc.local or /etc/rc.d/boot.local but both of these directories and files seem to not exist in ubuntu 5.10.  Also for the above code you need to use the sudo pretext but will this effect how it is executed at startup?  Any suggestions?  I've been to several forums about this and suprisingly recieved no answer or help.

---

### Post by stevestyle51 on 2006-05-25
Answered my own question.  There is a Sessions option in preferences that allows you to add whatever commands you want to add in the startup procedure along with its order.  I'm still curious how the sudo command will come into play, well I guess trial and error will have to take over from here.  I'll update the results forthose who are new to ubuntu, like I am.

---

