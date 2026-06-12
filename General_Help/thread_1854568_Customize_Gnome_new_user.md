---
title: "Customize Gnome new user"
date: 2011-10-04
forum: General Help
---

### Post by dfarquharson on 2011-10-04
I am configuring a class set of Ubuntu 10.10 computers for a computer lab. I need to customize the default Gnome new user setup. We have Centrify express installed to allow the students to log in using their student ID which is set up on a Windows Domain. The login process works fine, but the custom settings which I have set up for the panels, desktop and menus keep reverting back to the initial Ubuntu default.

I set up a new user (NEW) and configure everything the way I'd like it. I then login as a system administrator, run sudo nautilus, turn on view hidden files and proceed to copy everything from /home/new into /etc/skel. At this point I can log out and proceed to log in as another user (never logged in to this computer before but set up on the Domain). Everything works properly.

BUT . . 
after rebooting the computer, a new user gets the original default Ubuntu desktop.

Does anyone know how to stop Ubuntu from replacing the etc/skel setup with it's original default.

---

### Post by cariboo on 2011-10-04
Moved to General Help, as the question may not get answered in the Cafe.

---

### Post by fantab on 2011-10-05
> **dfarquharson said:**
> I am configuring a class set of Ubuntu 10.10 computers for a computer lab. I need to customize the default Gnome new user setup. We have Centrify express installed to allow the students to log in using their student ID which is set up on a Windows Domain. The login process works fine, but** the custom settings which I have set up for the panels, desktop and menus keep reverting back to the initial Ubuntu default.**


On my single user Desktop when faced with a similar problem I just opened **Startup Applications- options** and clicked *'save or remember running applications*' or something like that. Since Panel is an app this did the trick for me.

Hope this helps.

---

