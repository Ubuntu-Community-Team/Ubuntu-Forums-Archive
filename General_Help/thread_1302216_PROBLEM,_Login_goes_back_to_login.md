---
title: "PROBLEM, Login goes back to login"
date: 2009-10-26
forum: General Help
---

### Post by Cygoku on 2009-10-26
When I enter my password and hit Enter under Ubuntu at the login screen, it doesn't bring me to the desktop but to the login screen again, what can I try to fix this ?? 

Cygoku

---

### Post by Giblet5 on 2009-10-26
Power failure? Hard disk failure?

Were there any clues?

The login security mechanism is extremely simple and robust. If that has been corrupted, then little else can be trusted on that system.

Boot from a LiveCD image.

Mount whatever partition has /home on it.

Backup your home folder and other data you need to save.

Reinstall.

---

### Post by holycow131415 on 2009-10-26
to me, it sounds like you are not entering your username, hitting enter, then password, then hitting enter.

---

### Post by sleepy weasel on 2009-11-04
I'm having the same problem.  Inputing the user name and login multpile times it will not work.  I was also able to access the Terminal from the login scree (ctrl+alt+f1) and login there.  I created a second testuser for the and tried again and could not login on the 9.10 screen.  

My problems happened shortly after upgrading from 9.04 to 9.10.  I was playing a game, had a display problem and did a hard reboot.  Since then, I have been unable use the login screen.

---

### Post by Cygoku on 2009-11-04
> **sleepy weasel said:**
> I'm having the same problem.  Inputing the user name and login multpile times it will not work.  I was also able to access the Terminal from the login scree (ctrl+alt+f1) and login there.  I created a second testuser for the and tried again and could not login on the 9.10 screen.  

My problems happened shortly after upgrading from 9.04 to 9.10.  I was playing a game, had a display problem and did a hard reboot.  Since then, I have been unable use the login screen.Sorry to ear that you have the same problem.  Well, in my case, karmic alpha6 and rc1 were just fine until (like you), a game (sdlmame) froze my computer and hard to restart only to come accross this annoying problem.  I did reinstall a lot of time to narrrow down possibilities and troubleshooting.  

I found out that a repo I was adding was updating everything "X" and would corrupt the system files.  

The repo I was adding is this one : 

ppa:ubuntu-x-swat/x-updates

I hope it can be of any help sir.  

Cygoku

---

### Post by raczatt on 2009-11-05
Same problem. Login screen comes up in 1600x1200.
When I 1st logged in changed it to 1280x1024.
Next time I couldn't login in Gnome and Failsafe Gnome mode only in xterm mode. There I could change the resolution back, logged out and login was working again but desktop came up again in 1600x1200 .

---

