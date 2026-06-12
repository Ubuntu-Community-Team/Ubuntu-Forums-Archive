---
title: "Fetchmail won't start at boot"
date: 2011-11-12
forum: General Help
---

### Post by AlexBooton on 2011-11-12
Hi,

I've been posting about this problem for a few weeks without much help.

But I just noticed there are NO links to /etc/init.d/fetchmail in any of the /etc/rcN.d directories (where "N" = 0,1,...5).  

/etc/init.d/fetchmail does exist.

I don't have a clue how this happened but I did use Synaptic to reinstall fetchmail a few days ago.  (It didn't help with the won't start at boot problem).

I don't know if the links were there before the re-install or not but considering that it won't start at boot I'm guessing they have always been missing.

What's the easiest way to fix this?

Thanks

---

### Post by AlexBooton on 2011-11-13
Hi,

I installed fetchmail on another machine and it installed a link /etc/rc2./S99fetchmail

Is this correct?  Why isn't it S02fetchmail?

Thanks

---

### Post by SeijiSensei on 2011-11-13
> **AlexBooton said:**
> Hi,

I installed fetchmail on another machine and it installed a link /etc/rc2./S99fetchmail

Is this correct?  Why isn't it S02fetchmail?

Thanks

The numbers refer to when the script is run during boot.  S02 would likely be too early in the process because the network will not yet be running.  S99 is used to run custom scripts after everything else has finished.

An easier method is to put the fetchmail command in /etc/rc.local.  This file is executed after everything in the init directories have completed.

---

### Post by AlexBooton on 2011-11-13
> **SeijiSensei said:**
> The numbers refer to when the script is run during boot.  S02 would likely be too early in the process because the network will not yet be running.  S99 is used to run custom scripts after everything else has finished.

An easier method is to put the fetchmail command in /etc/rc.local.  This file is executed after everything in the init directories have completed.

Thanks for the info. That's reassuring.

I did try putting a command in rc.local.  In fact I tried it two different ways:

[INDENT]fetchmail -d 60 -f /etc/fetchmailrc
and
service fetchmail restart
[/INDENT]
Neither worked.  I have no idea why.

Thanks for your help.

---

### Post by AlexBooton on 2011-11-13
Hi,

Well I think I fixed it.  I created a link to /etc/inet.d/fetchmail; copied it to each of the rcN.d directories; and renamed them as I found them named on another machine.  

A bit of a chore but it seems to be working.

I'm concerned about why these links weren't there in the first place.  Could this be a bug in the install script?

Thanks to all (in this thread and previous ones) for your help!

---

