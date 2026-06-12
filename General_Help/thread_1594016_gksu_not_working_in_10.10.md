---
title: "gksu not working in 10.10"
date: 2010-10-11
forum: General Help
---

### Post by Danny Dubya on 2010-10-11
I can enter my password just fine to log into the system, and using sudo from a terminal also works, but "gksu" does not. It tells me my password is incorrect. That means Synaptic doesn't work unless I "sudo synaptic" from the terminal.

Anyone else happen to encounter this yet, or is it just me? I started with a clean install of Kubuntu 10.10, which I later installed ubuntu-desktop over and then removed. Would that possibly make a difference here?

---

### Post by andrewthomas on 2010-10-11
If you are on kubuntu you want kdesudo,


[http://packages.ubuntu.com/maverick/kdesudo](http://packages.ubuntu.com/maverick/kdesudo)

---

### Post by kerry_s on 2010-10-11
> **Danny Dubya said:**
> I can enter my password just fine to log into the system, and using sudo from a terminal also works, but "gksu" does not. It tells me my password is incorrect. That means Synaptic doesn't work unless I "sudo synaptic" from the terminal.

Anyone else happen to encounter this yet, or is it just me? I started with a clean install of Kubuntu 10.10, which I later installed ubuntu-desktop over and then removed. Would that possibly make a difference here?

it's "gksudo" not "gksu", ubuntu is a sudo system. gksu is the gui for su, so even su won't work, in ubuntu its sudo su.

---

### Post by mc4man on 2010-10-12
If you  wish to use gksu then open the configuration editor (gconf-editor

apps - gksu - and make sure sudo mode is enabled.

---

### Post by kerry_s on 2010-10-12
> **mc4man said:**
> If you  wish to use gksu then open the configuration editor (gconf-editor

apps - gksu - and make sure sudo mode is enabled.

"**gksu-properties**" is the command to change the settings.

---

### Post by Danny Dubya on 2010-10-12
> **kerry_s said:**
> it's "gksudo" not "gksu", ubuntu is a sudo system. gksu is the gui for su, so even su won't work, in ubuntu its sudo su.
Then why don't you go lecture Canonical about that? I found "gksu synaptic" as a built-in menu entry, not "gksudo synaptic". They must not know their own system very well, according to you.

By the way, I know Ubuntu's a sudo system, as my saying "... and using sudo from a terminal also works ..." in the first post would indicate.

Anyway, after running an update the next morning, the issue seems to have disappeared on its own for whatever reason. Thanks for your responses, all.

---

### Post by drapsag on 2010-10-12
same here, installed fresh server system with ubuntu-desktop and found this gksu in the command that calls synaptic from the menu

Maybe someone can add this as issue in launchpad...

---

### Post by kruykaze on 2010-11-27
How is this solved? i still have this issue in 10.10

---

### Post by Mocker on 2010-12-27
I hit this after creating a virtual machine using a minimal install CD and the Attobuntu install script. Since this is just a virtual machine used internally, I solved the problem by manually setting the root password to be the same as my login password like so:

```

sudo passwd root
[sudo] password for yourusername: 
Enter new UNIX password: 
Retype new UNIX password: 
```

The problem is, of course, you now have a password for root that might be cracked, or you may forget to manually set the password for root if your own password become compromised, and tons of other insecurities that this probably creates. For me, in this use, it's good enough.

---

