---
title: "KDE System Settings Administrator Mode/su command not working"
date: 2006-01-26
forum: General Help
---

### Post by fletch on 2006-01-26
I don't know exactly when the problem arose, but when it appeared, I definately began to take notice. I'm not one to usually need to change su-required setting all the time, but when I tried to goto system settings > Network Settings to change to a Static IP, i entered my user password in the box. No go. The password box would disappear after I entered it, and the settings would still be disabled/greyed out. So then next I opened up a terminal, and attempted the SU command. It prompted me for a password, so I used my user password. No go. However, the SUDO command still works, and the SUDO -i command will give me root access. Using this, i entered the PASSWD command to change the root password, thinking that might help. Nope.

I'd really like to have access to my system settings!

---

### Post by seakiwi on 2006-01-26
[QUOTE=fletch]I don't know exactly when the problem arose, but when it appeared, I definately began to take notice. I'm not one to usually need to change su-required setting all the time, but when I tried to goto system settings > Network Settings to change to a Static IP, i entered my user password in the box. No go. The password box would disappear after I entered it, and the settings would still be disabled/greyed out. So then next I opened up a terminal, and attempted the SU command. It prompted me for a password, so I used my user password. No go. However, the SUDO command still works, and the SUDO -i command will give me root access. Using this, i entered the PASSWD command to change the root password, thinking that might help. Nope.

I'd really like to have access to my system settings![/QUOTE]

I had exactly the same problem the other day and thought it was something I'd done to screw something up. Evidently it's a bug that's already been reported. I'll go see if I can track down the thread and post a link back here for you. BRB!

EDIT: [http://www.dslreports.com/forum/remark,15311618](http://www.dslreports.com/forum/remark,15311618)

I've also stumbled across a thread at a different forum about this - can't find it right now but if I do I'll post it.

---

### Post by fletch on 2006-01-26
A bug you say? Well thats just terrible. I would hate to have to re-install the OS again, this has been one of the best distros I've ever used.

EDIT: Just to clarify, this goes for any application in Kubuntu that requires a su password. That being said, I'm really limited with Kubuntu. Should I just backup and re-install?

---

### Post by codejunkie on 2006-01-26
right click on the kmenu choose menu editor add a new menu item name it something like rootkcontrol and for the command enter 
```
kdesu kcontrol
```to edit network setting go into rootkcontrol/Internet & Network/Network settings this will let you edit the network settings as root when it asks for a password enter yours not the root password hope this helps.

---

### Post by Jucato on 2006-01-27
Maybe you could also try to upgrade to KDE 3.5 if you still haven't. It might resolve some of these bugs.

---

### Post by fletch on 2006-01-27
Right on! Just did a mass upgrade with adept, rebooted my system, Administrator mode works fine now! I'm hoping this was a KDE error though, and not a user error lol, because I honestly don't know what possible settings I could have changed to have it abruptly do this to me.

Thanks a lot guys!

---

### Post by Jucato on 2006-01-27
I think it was really a KDE error. It happened to me many times. Almost panicked, until I came across the KDE 3.5 upgrade.

There is one more thing that you'll probably notice, which I also think is a KDE error. Sometimes, apps that are run w/ kdesu (adept, Login Manager, kdesu kate, etc) will not launch immediately or will not launch at all. But if you look at KSysGuard (Ctrl+Esc), the kdesu process still lingers around. I'm pretty sure it's a KDE bug, so don't panic if it ever happens. :D

---

### Post by fletch on 2006-01-27
Alright. Thanks for the heads up.

Just wondering though, has this been a KDE error running with Ubuntu or just a KDE error in general?

---

