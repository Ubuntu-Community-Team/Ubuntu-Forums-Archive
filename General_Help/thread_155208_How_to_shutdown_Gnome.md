---
title: "How to shutdown Gnome?"
date: 2006-04-04
forum: General Help
---

### Post by Rory on 2006-04-04
Okay, this is what I'm trying to do:
I'd like to hit the the Logout button in Gnome, for it to pop-up "Reboot" or "Shutdown" and then for it to simply do it, like it does in KDE.  

In Gnome, it then takes you to the GDM screen, where you sign-off.  Way too many button clicks.  Yes, some of you will suggest I just don't turn off my computer, but I pay my electricity bill, not my parents. :)  

So, it was suggested to me that I do a shortcut with the command:
**sudo shutdown -h now**

No dice.  This works in terminal but not as a shortcut.  So, I tried:
**gksudo shutdown -h now**

No dice.  The issue is the need to type in a password.  So, I tried this as the shortcut command:
**echo mypassword | sudo shutdown -h now**

No dice.  I could disable the need for a password to go root in Ubuntu, but that's overkill and I like the security.  Just don't need it for signing off.  

Can anyone suggest another way to do this so I can do a simple, one-click shutdown in Gnome that will power my computer off?

Thanks,
Rory

---

### Post by nanotube on 2006-04-04
if you go through the menu, System> Logout, that will present you with a window of options, one of which is to shut down... so i am not sure what your problem is.

---

### Post by Rory on 2006-04-04
Ah, my problem, as you put it, would be that I don't have the option under Menu>System in Ubuntu Breezy with Gnome.  But, that's exactly the option I'm looking for.

When I go Menu>Logout and select it, it just signs me out of Gnome and brings me to the GDM signin/signout screen, which is the step I'm trying to bypass and which you can bypass when you do sudo shutdown -h now from terminal.

R.

---

### Post by nanotube on 2006-04-04
hmm... i think if you go to System>Preferences>Sessions, and there make sure the box called "ask on logout" is checked, you will force it to present you with the menu where you can choose "shutdown". 
try that. :)
if not, we will have to look for it somewhere else.
i suspect that you simply saved your choice of "logout" at some point, so that it doesnt ask you anymore. we just need to clear that save, and it should start asking you what you want to do...

---

### Post by aysiu on 2006-04-04
It sounds as if you're using Gnome with KDM.
Maybe [this thread](http://www.ubuntuforums.org/showthread.php?t=142183) might help.

---

### Post by Rory on 2006-04-06
nanotube and aysiu, that was it!!  Thank you to both of you!!

nanotube, that was under Sessions wasn't checked.  You're right and that has resolved my problem.  I just assume this was a Gnome usability issue.  

And aysiu, you are correct.  Until a few days ago, I was using KDM to boot in to Gnome, as I've just left KDE.  So, that appears to have been the wrinkle,  And the thread you noted would have been perfect if I nanotube hadn't have pointed out the "sessions" checkbox solution.  I'll keep that thread handy for when I next try out KDE 4.0.

Again, thank you to both of you!

Rory

---

### Post by nanotube on 2006-04-06
you're welcome. have fun. :)

---

