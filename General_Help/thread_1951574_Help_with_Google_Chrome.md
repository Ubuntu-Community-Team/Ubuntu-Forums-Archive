---
title: "Help with Google Chrome"
date: 2012-04-02
forum: General Help
---

### Post by mshumer on 2012-04-02
Help!
I'm sure there are some smart people out there that have seen this one. We're using an Acer Aspire One loaded with Ubuntu 10.10. My friend says she went to Match.com using Chrome and suddenly it started opening blank pages. I shut down the machine with 137 blank tabs opened!

After a reboot, I found all these references to an .exe file (don't remember the name) which I deleted. I unloaded chrome then did an apt-get autoremove, clean and purge. I couldn't find a .chrome system folder inside /home/username$. Somehow the menus had been deleted from desktop too. 

I did a clean install of 11.10 with xfce4. Installed chrome and it still continues to open blank tabs. I have to shut down the computer to get it to stop. 

Can anyone suggest a solution???

thanks.

---

### Post by thaelim on 2012-04-02
The user's data for Chrome is stored under ~/.config/google-chrome. Try removing that directory and then starting Chrome again.

---

### Post by fiatveritas on 2012-04-03
There's two things you can install: Ad Block Plus and a program that blocks scripts from automatically running. The reason I'm suggesting these two add-ons/extensions (for Chrome) is because both prevent ads or scripts from running on your browser. Ad Block is easy to use because you can disable it; "No Script" programs are a little more difficult to use because you need to configure what website you allow to run scripts on your browser. Scripts, in general, aren't bad; it's people who are bad. That said some scripts are bad, so preventing scripts from automatically running will keep you absolutely safe.

Try Ad Block Plus and if that isn't enough try a "No Script" program.

---

### Post by linuxmatt7 on 2012-05-06
This happened to me all the time on Xubuntu 12.04. It can easily be fixed by running the update manager to update Google Chrome. If it still does it (which it didn't to me) just remove Google Chrome, and try a different web browser.

---

