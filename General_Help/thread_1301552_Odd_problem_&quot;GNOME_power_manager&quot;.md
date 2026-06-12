---
title: "Odd problem &quot;GNOME power manager&quot;"
date: 2009-10-26
forum: General Help
---

### Post by Ocarina on 2009-10-26
I would appreciate it, if anyone could give me hand.
Before you ask, yes, I've tried reinstalling Ubuntu to fix this problem of mine.

The problem:

I've installed Ubuntu, like normal, used it, downloaded a few apps and so on.
Turned off my PC and went to bed. Then the next day, I get this error message and can't log in to Ubuntu:
**"The configuration defaults for GNOME Power Manager have not been installed correctly, Please contact your computer administrator"**
There is also no background, it's only black. When I try to log in, I just see the Ubuntu start up loading screen again, then I see the log in screen, it's just a loop.
Every dam time I try to log in, it just goes back to the loading screen, then the log in screen.

VERY ANNOYING.

I tried reinstalling, but the same dam thing happens, it works the first time I use Ubuntu, but when I shut-down and start it up again, the same thing happens...

Anyway, thanks for reading, I hope you have an idea, I don't...

[B]Ubuntu: 9.10
GRUB: 1.97[/B]

---

### Post by TenPlus1 on 2009-10-26
Strange problem, make sure your power settings are enabled in the bios and give it another go...  failing that you could always disable power management in services and that may help...

---

### Post by khelben1979 on 2009-10-26
What version of Ubuntu?

---

### Post by Ocarina on 2009-10-26
> **TenPlus1 said:**
> Strange problem, make sure your power settings are enabled in the bios and give it another go...  failing that you could always disable power management in services and that may help...
I'll have to take a look at the power settings, but I don't think it has anything to do with it, especially because I was able to get into it once.
How would I disable it? I can't log in, is there anything I can type into GRUB?


> **khelben1979 said:**
> What version of Ubuntu?
Sorry, I should have said.
[B]Ubuntu: 9.10
GRUB: 1.97
[/B]

---

### Post by ranch hand on 2009-10-26
There seems to be some problem with this "looping" in the GDM.

Here is a current thread from the "testing" forum;
[http://ubuntuforums.org/showthread.php?t=1301185#post8165849](http://ubuntuforums.org/showthread.php?t=1301185#post8165849)

You might try logging into the "failsafe gnome" session.  Click on you login and the options come up on the bottom bar.  Click on sessions and you should see the "failsafe gnome" option.  Then try entering the password and logging in.

Once in you can look for the power configuration stuff.

---

### Post by Ocarina on 2009-10-30
> **ranch hand said:**
> There seems to be some problem with this "looping" in the GDM.

Here is a current thread from the "testing" forum;
[http://ubuntuforums.org/showthread.php?t=1301185#post8165849](http://ubuntuforums.org/showthread.php?t=1301185#post8165849)

You might try logging into the "failsafe gnome" session.  Click on you login and the options come up on the bottom bar.  Click on sessions and you should see the "failsafe gnome" option.  Then try entering the password and logging in.

Once in you can look for the power configuration stuff.

Sorry for the late reply.

I'll get back to you after trying some things from the "looping page", you sent me.
BTW, options doesn't seem to be coming up, at the login screen...

---

### Post by ranch hand on 2009-10-30
You need to hit enter or click on the user to get that stuff up.

---

