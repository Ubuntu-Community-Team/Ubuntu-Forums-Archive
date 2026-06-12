---
title: "Can't Edit or Add Startup Programs"
date: 2010-01-06
forum: General Help
---

### Post by vyszard on 2010-01-06
I'd like you to know that I'm completely new to ubuntu. Just install it a couple of days ago.

I have a bit problem with startup here, everytime I change anything in System > Preferences > Startup Applications it just keep coming back to default. I unchecked Penmount Utility, and it's checked again after next boot. Same thing happen when I add Guake Terminal. When I reboot, it's not there anymore.

So basically, it seems that I can't configure my startup programs.

---

### Post by JC Cheloven on 2010-01-07
I'm not sure about the guake terminal (never used that), but if you have Penmount at startup, you probably have quite a special hardware. It could help to know what hardware is it. 
A tablet pc, I guess?

---

### Post by jahisthebalance on 2010-03-05
I am experiencing the same issue.  I want to stop Maximus. I uncheck it, I login and out, reboot entirely even, and boom it's still checked and running on startup.

---

### Post by tylerspaska on 2010-05-16
I've experienced this problem too. The way to fix it is to change the ~/.config/autostart folder from root permissions to user permissions. 

Open a terminal an type

```
sudo chown -R $USERNAME $HOME/.config 
```

Enter your password and hit return. Now you should be able to add and remove programs from in the *Startup Applications Preferences*. 

$USERNAME is a variable for your username and $HOME is a variable for the location of your home folder.

---

