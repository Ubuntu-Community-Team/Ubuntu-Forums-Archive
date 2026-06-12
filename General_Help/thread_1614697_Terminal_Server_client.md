---
title: "Terminal Server client"
date: 2010-11-05
forum: General Help
---

### Post by nmyrick on 2010-11-05
I get the following error when trying to log on to Windows Servers with Ubuntu Terminal Server.  I get the logon screen, and it allows me to enter the username and password, but then I get this error.

**[SIZE=1]'The requested operation cannot be completed because the Terminal connection is currently busy processing a connect operation'[/SIZE]**

I have a Windows XP virtual machine on the same computer, and it has absolutely no problem logging in to these machines with Remote Desktop.

Can anyone help me solve this issue?  I would like to be able to do this through Ubuntu.

---

### Post by dcstar on 2010-11-06
> **nmyrick said:**
> I get the following error when trying to log on to Windows Servers with Ubuntu Terminal Server.  I get the logon screen, and it allows me to enter the username and password, but then I get this error.

**[SIZE=1]'The requested operation cannot be completed because the Terminal connection is currently busy processing a connect operation'[/SIZE]**

I have a Windows XP virtual machine on the same computer, and it has absolutely no problem logging in to these machines with Remote Desktop.

Can anyone help me solve this issue?  I would like to be able to do this through Ubuntu.

Every single Google hit I have read says that this is a Windows server issue where there is a locked up connection preventing a new connection from being set up.

I use the Ubuntu TS Client to connect to Windows boxes with no problem at all.

---

### Post by nmyrick on 2010-11-06
> **dcstar said:**
> Every single Google hit I have read says that this is a Windows server issue where there is a locked up connection preventing a new connection from being set up.

I use the Ubuntu TS Client to connect to Windows boxes with no problem at all.

But if that's the case, why can I connect to them with my Windows XP virtual machine that is installed on the same machine as the Ubuntu, but I can't connect through Ubuntu Terminal Services?

---

### Post by nmyrick on 2010-11-06
> **nmyrick said:**
> But if that's the case, why can I connect to them with my Windows XP virtual machine that is installed on the same machine as the Ubuntu, but I can't connect  through Ubuntu Terminal Services?

I see why this is happening now.  There is a disconnected user in terminal services manager that was logged on from my computer, but when I try to log that user off, it doesn't work. I also can't get rid of that user when resetting.  So how do I get rid of that user?  Do I try restarting the terminal services service? If so, I cant do that remotely.  Well, I probably can, but it is risky, in the event that it doesn't come back up.

Or, is the only option to restart the server, which I obviously can't do without good reason.

---

