---
title: "Suspend no longer working"
date: 2010-02-23
forum: General Help
---

### Post by bkcevilmonkey on 2010-02-23
Hello all,

I've managed to use ubuntu for many years without posting a question on the forums, but this has stumped me.
I have a compaq cq60 laptop, i installed the 64bit version of ubuntu 9.10, everything was working perfectly.

Then I installed a program called jupiter [http://sourceforge.net/projects/jupiter/files/](http://sourceforge.net/projects/jupiter/files/) and ever since then it would no longer let me standby or hibernate.  When I press the button to suspend, it blackens the screen and if i move the mouse it asks for the password (as if it locked the screen instead of suspending).

I googled for a solution, and tried many things.  First, i tried pmi action suspend.  It waits a long time in the terminal then returns this:

```
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: 
the remote application did not send a reply, 
the message bus security policy blocked the reply, 
the reply timeout expired, or the network connection was broken.
```then I tried typing in /usr/sbin/pm-suspend but it returns nothing and does nothing.

Next I tried s2ram and s2ram --force. Neither worked.  It returned this:

```
me@my-laptop:~$ sudo s2ram
[sudo] password for me:
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Hewlett-Packard"
    sys_product  = "Compaq Presario CQ60 Notebook PC"
    sys_version  = "F.35"
    bios_version = "F.35"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.
```I am stumped by this, any help would be greatly appreciated.  I'm confident that a reinstall would fix all my problems but that would be a big hassle which I'd like to avoid.

ps. uninstalling jupiter does not fix this problem.

---

### Post by manequin on 2010-02-24
I had same problem and this was a solution:
```
sudo rm /etc/pm/sleep.d/00-jupiter-wifi
```

---

### Post by bkcevilmonkey on 2010-02-24
Thank you! that worked perfectly.

---

### Post by swissz on 2010-03-01
Hi!
I just had a similar problem, apart the fact, that I don't have the jupiter software on my machine. I use the "pmi action suspend" command to suspend my desktop. It was always working fine. Today my computer just didn't react to this command. I tried the s2ram, and s2ram --force commands too, the later seemed to work, but by resuming the computer it crashed, I had to turn the desktop off by the power button - not even SysRq keys worked. Since then the original "pmi action suspend" has worked again. Strange...

---

### Post by asndo on 2010-08-24
I have the same situation.
I think it's "the message security policy" thing and the solution should be similar and easy for some pros, but I'm a newbe.

in /etc/pm/suspend.d i have 3 files and deleting neither solves something (10_grub_common 10_unattended-upgrades-hibernate action_wpa)

More details: my laptop is Asus Eee PC 1201HA and no suspend tool apart from "pmi action suspend" have ever worked for it. The command refused to work after I installed vlock and tried to lock the screens and suspend my laptop at once (I don't know any better way to do this) with command like:
[I]echo "pmi action suspend" | at now + 1 minutes
vlock -a[/I]
At first it destroyed my ability to suspend at normal user profile, and with further playing with that code on sudo account I became unable to suspend as root as well.

Like in the aforementioned case the situation goes back to normal after a reboot.

---

