---
title: "Cant Install Wine"
date: 2006-04-19
forum: General Help
---

### Post by Muag on 2006-04-19
Ok, im following the directions at [www.winehq.com](www.winehq.com) and im trying to install it using the terminal...this is what is says to do.
"Switch to root by typing 'su'. If you are an Ubuntu user, you can instead precede each command with 'sudo'. Now, use your favorite text editor to open the file /etc/apt/sources.list or use the console editor by typing 'nano /etc/apt/sources.list' and then add the following lines to the end:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/"

so when i try to switch to root by typeing 'su', it ask for the password then says      "su: Authentication failure
Sorry."

so how can i fix this?

---

### Post by skymt on 2006-04-19
That problem is solved easily, simply by reading the documentation you quoted more carefully: "If you are an Ubuntu user you can istead precede each command with 'sudo'". This means use sudo instead of using su, which isn't very useful in Ubuntu. If you like, you can get just about the same effect as su, with the command "sudo -s".

---

### Post by Muag on 2006-04-19
thanks, that worked

---

