---
title: "keyboard not working with citrix"
date: 2011-08-22
forum: General Help
---

### Post by cheesebreath on 2011-08-22
Hello everyone

I have been using citrix to log into work for quite some time now. Recently I ran into a problem where the keyboard stops working after some time. The link below from a citirx forum describes the issue.

[http://forums.citrix.com/message.jspa?messageID=1402842](http://forums.citrix.com/message.jspa?messageID=1402842)

They suggest:

The work-round is to edit the file config/module.ini below the client's installation directory (usually /usr/lib/ICAClient), find the line "UseLocalIM=True" and change the value to "False".

My issue is that this a root file and I don't want to compromise my system.

So my question is should I try this and if so could somebody lead me by the hand as to how; using the sudo and I believe chmod commands.

Thanks

---

### Post by cheesebreath on 2011-08-22
I forgot to add that I can locate the file. I just need help modifying it as i need root access to do so

Thanks

---

### Post by cheesebreath on 2011-08-22
never mind figured it out myself with help from following link

[http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008)

---

