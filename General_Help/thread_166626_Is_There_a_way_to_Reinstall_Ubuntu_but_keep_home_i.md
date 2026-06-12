---
title: "Is There a way to Reinstall Ubuntu but keep /home in tact?"
date: 2006-04-26
forum: General Help
---

### Post by drpolish on 2006-04-26
I have a /home directory on a different partition, but last time that i  tried to reinstall ubuntu i had problems logging into my account, and therefore just started over. I want to reinstall ubuntu on my laptop, and i did the same, so how can i install ubuntu and keep my logins, themes, gnome configurations and etc. in tact?

---

### Post by jazzmuzik on 2006-04-26
If my experience is any indication there are some problems reusing an old account. From what I can tell the problem is with gnome settings. I also wonder if temporary files in /tmp are also part of the problem.

It's good that your /home mount is on its own partition. The main thiing is to not format that partition when you reinstall.

Here's what I do, and it may be above and beyond what is actually necessary.

When I'm ready to install (or reinstall) a new version of Linux I'll log out of my account to the main login screen. Then I'll press Ctrl-Alt-F1 to get a text login and then I'll log in. I'll go to /home (cd /home) and I'll rename my user directory to anything else. (sudo mv jazz/ jazz-old/) Then I reboot (type 'reboot'), perform the new install from CD and specify my usual user account (jazz). Once everything is installed I'll copy files from my old jazz account to the new account. This has always worked well for me. It just takes a little bit of time to copy things over. The reason for copying is I only copy the important things and let the rest start fresh. It's a PITA, but I've never seen a solution for the problems like you've encountered. But perhaps somebody knows a better solution.

Last thing, after copying all the files from the old acct to the new one you may need to fix the file ownership. DO this:

sudo chown -R jazz:jazz /home/jazz

Replace 'jazz' with your user account name.

---

### Post by drpolish on 2006-04-26
Thats a nice ghetto solution, and i'll most likely do it that way, but if anyone out there does something better then help is appreciated.

and of course i dont format the drive during install lol

---

### Post by jazzmuzik on 2006-04-26
This might be a simpler solution:

Reinstall Linux and specify the same /home user account that already exists. After installation when you get to the login screen, THEN do the Ctrl-Alt-F1 thing, log in and delete the gnome settngs: 

rm -rf /home/user/.gnome*

Exit (Ctrl-D, Alt-F7). Now log in normally, gnome settings are recreated, and it should work.

---

