---
title: "Gnome3 installed + reboot = Stopping System V runlevel Compatibility. Help Please"
date: 2011-09-26
forum: General Help
---

### Post by maddbaron on 2011-09-26
I researched and it looks like I need to reinstall my ati graphics, fglrx software because I'm getting a black screen with those words. I can't even boot up in safe graphics mode.

Can someone tell me how to access terminal from safe and how to install the ati/fglrx software?

or if i remove the gnome3 software will it revert back to my unity interface and if so how do I do that from terminal in safe mode?

Thanks in advance.

---

### Post by maddbaron on 2011-09-27
bump for help

---

### Post by maddbaron on 2011-09-27
bump for help please

---

### Post by bholzer on 2011-10-16
Sorry to be so late to the rescue, but I came up with a solution that worked for me. 
1. Ctrl+alt+f1 and login.
2. After logging in I ran sudo dkpg --configure -a
3. This will probably run for a while, and spit out some errors, but it will work for the most part. Once it's done, run sudo apt-get dist-upgrade
4. Once it's done, sudo apt-get update, and then reboot. 
5. Still having a little trouble with booting, because everytime I start up I have to ctrl+alt+f1 and startx

---

