---
title: "Restore the default Gnome Login"
date: 2010-04-03
forum: General Help
---

### Post by nathbfreak on 2010-04-03
I installed KDE as an alternative desktop.(I still have gnome) When I rebooted my system it showed the KDE login screen. How do I restore the default Gnome login screen. I run Lucid.

---

### Post by DeMus on 2010-04-03
> **nathbfreak said:**
> I installed KDE as an alternative desktop.(I still have gnome) When I rebooted my system it showed the KDE login screen. How do I restore the default ubuntu login screen. I run Karmic.

At the log-in screen you can choose options and there you can make Gnome the default again.

---

### Post by scacinto on 2010-04-27
the poster didn't mean the desktop environment, but the actual login screen itself.  I did the exact same thing and still can't find an answer.  can someone state in what config file the login screen is set?  I updated to Lucid hoping for a new login ... now i'm stuck with hideous default gdm login :P

---

### Post by Craig Robach on 2012-03-31
Same here. I wanted the KDE environment, now I just wish to switch the login screen back to gnome.




PS: I would like people to join my website.


Membership sites I own:

Srilzone Membership
[http://srilzone.webs.com/]("http://srilzone.webs.com/")

Social Srilzone
[http://socialsrilzone.webs.com/]("http://socialsrilzone.webs.com/")

for all the available software I create for windows, go here:
[http://srilzone.weebly.com/downloads.html]("http://srilzone.weebly.com/downloads.html")

---

### Post by grahammechanical on 2012-03-31
I think that Kubuntu uses kdm. I know Ubuntu used to use gdm but now it uses lightDM.

When there was an issue early in 12.04 where LightDM would not let you log in, we issued a command to stop lightDM followed by a command to start gdm and we used gdm until the problem was fixed.

That is the command that you need (I think). You must make sure that gdm is installed on your system. 

Regards.

---

