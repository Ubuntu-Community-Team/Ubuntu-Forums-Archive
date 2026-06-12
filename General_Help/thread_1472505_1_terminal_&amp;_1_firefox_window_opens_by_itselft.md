---
title: "1 terminal &amp; 1 firefox window opens by itselft at startup"
date: 2010-05-04
forum: General Help
---

### Post by midjean on 2010-05-04
Hi,

since few days, when I start my ubuntu karmic on laptop dell vostro 1000, gnome opens me one terminal window, and one firefox window at startup... I've checked on apps which start automatically on startup and there is nothing wrong... I didn't find any other threads about this problem and I really want to fix it !
Does anyone already had this problem ? or have an idea ?
Thanks,

Jean

---

### Post by MSwal2846 on 2010-05-04
I'm not seeing the terminal, but I am seeing the Firefox opened up.  Infact, I'm unable to kill it.  It remains present regardless...

Mark

---

### Post by uRock on 2010-05-04
Go to System> Preferences> Startup Applications and unclick those in the from the menu.

---

### Post by MSwal2846 on 2010-05-04
In my case, Firefox is NOT in my startup list ... I had checked that and checked again after I read your post.  Any other ideas?

Mark

---

### Post by uRock on 2010-05-04
Clicking the Options tab and selecting to Remember Currently Running Application and/o should fix it.r unclicking the box there.

---

### Post by MSwal2846 on 2010-05-04
That option is NOT checked.

---

### Post by uRock on 2010-05-04
I am not sure what else to try. For now you can add the Force Quit button to a panel and use it to kill the program if needed.

---

### Post by uncleV on 2010-05-04
Another Idea:
Open applications you want to start automatically at login.
Close those apps that you don't want automatically started.

Go System-->Preferences-->Startup Applications and chose tab "Options" and then click on button "Remember Currently Running Application".

Logout then login to see if it works.

If you don't want any app autostarting then do that procedure with no application opened.
Just tried it and on my computer it works.

[COLOR=Blue]Edit:[/COLOR] Duplicated uRock's advice but it wasn't there when I began to post.

---

### Post by midjean on 2010-05-04
Hello uRock,

1) when I uncheck policykit and I restart gnome, nothing happend: policykit is recheck and terminal / firefox still opens by themselves.

2) when I uncheck policikit and I keep settings in option tab, restart gnome: policykit still uncheck and terminal / firefox do not open.

So, thanks, it works for me ! But now, new question: what is policykit ? is it safe to uncheck it ?

---

### Post by MSwal2846 on 2010-05-04
Found it ... my "problem" was that it was always present on my AWN launchpad.  I had assumed that it was there because it had, somehow, been started.  I noticed, however, that it didn't appear on the launch panel, but it did persist on the AWN Launcher.  The I realized that I had it marked to persist on the AWN launcher (didn't realize that I had done that).

Net:  user error!

---

### Post by midjean on 2010-05-04
bump :confused:

---

