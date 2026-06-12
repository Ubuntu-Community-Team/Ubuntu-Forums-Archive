---
title: "Hardy: How do I start X without GDM?"
date: 2010-06-15
forum: General Help
---

### Post by Cool Javelin on 2010-06-15
I would like to start the x graphical interface without using GDM.

I may be using the wrong terms here for x. Maybe it is called xdm or x11 or something.)

I have set GDM to login without asking me for a password (I am the only user of this machine.) Sometimes, it still pops up the GDM login screen and if I select "actions" "reboot" (my memory tells me that is what it was,) it will reboot without asking to login, but the fonts are all wrong. If I select "apps" "restart" and it DOESN'T ask for my login, all is OK.

I would like to uninstall GDM, and place whatever GDM uses to start the graphical interface into the /ect/rc2.d startup scripts.

I know GDM does other stuff then just logs me in and starts the graphical user interface, and I think I would like to maintain some of that, but I think I would like to manually insert the startup sequence in the startup scripts.

Question one, can someone tell me where to look to find out what GDM is doing now so I can attempt to replicate it?

#2, does someone know the startup script line(s) to start the x server and graphical interface without GDM?

I think this has bees asked before, but it seems hard to search older posts.

Thanks for your help,
Mark.

---

### Post by bodhi.zazen on 2010-06-15
You boot to the command line. You will get a log in prompt.

Log in and use

```
startx
```

---

### Post by guy-rouillier on 2010-06-16
What is the proper way to tell Ubuntu 10.4 to boot to the command line?  I installed the server version, then installed LXDE, which installed lxdm.  Since this is a server, I'd like it to just boot to the command line and run startx on those rare occasions when I need it.  But I can't figure out the proper way to disable lxdm.  Do I just uninstall it, or is there some configuration setting somewhere that I can tell Ubuntu not to start up lxdm?  In the old days, I just change the runlevel, but that doesn't work any more.

Thanks.

---

### Post by bodhi.zazen on 2010-06-16
> **guy-rouillier said:**
> What is the proper way to tell Ubuntu 10.4 to boot to the command line?  I installed the server version, then installed LXDE, which installed lxdm.  Since this is a server, I'd like it to just boot to the command line and run startx on those rare occasions when I need it.  But I can't figure out the proper way to disable lxdm.  Do I just uninstall it, or is there some configuration setting somewhere that I can tell Ubuntu not to start up lxdm?  In the old days, I just change the runlevel, but that doesn't work any more.

Thanks.

Runlevels 2-5 have been the same for some time now.

Yes you need to disable LXDM or remove it. I am not sure if lxdm is called from upstart (/etc/init) or /etc/init.d with links to run levels.

---

### Post by guy-rouillier on 2010-06-16
Thanks, I found an alternate solution here that doesn't require removing any packages or figuring out how to disable whatever DM you have installed:

[http://ubuntuforums.org/showthread.php?p=9470029#post9470029](http://ubuntuforums.org/showthread.php?p=9470029#post9470029)

This would be good material for a wiki as the question seems to come up from time to time.

---

### Post by sisco311 on 2010-06-16
EDIT: Never mind! I'm slow :)


> **guy-rouillier said:**
> In the old days, I just change the runlevel, but that doesn't work any more.


lxdm is started by an Upstart job: /etc/init/lxdm.conf

To boot directly into text mode add **text** to the default kernel parameters.

---

### Post by bodhi.zazen on 2010-06-16
> **sisco311 said:**
> EDIT: Never mind! I'm slow :)




lxdm is started by an Upstart job: /etc/init/lxdm.conf

To boot directly into text mode add **text** to the default kernel parameters.

Nice one =)

---

### Post by sisco311 on 2010-06-17
> **bodhi.zazen said:**
> Nice one =)

Yep :)

It works with the display managers which are using Upstart jobs (Karmic and newer): gdm, kdm and lxdm. 

slim, xdm and wdm are still using System-V style init scripts.

---

