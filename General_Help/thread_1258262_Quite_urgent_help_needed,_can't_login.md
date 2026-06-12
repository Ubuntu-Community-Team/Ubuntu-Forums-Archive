---
title: "Quite urgent help needed, can't login"
date: 2009-09-04
forum: General Help
---

### Post by frogbrains on 2009-09-04
Sorry for the mental title, but it is a bit urgent.

Right, so, basically, when Ubuntu goes to the login screen, a message appears straight away saying "Authentication failed".  When I press ok, it re-appears instantly, leaving me unable to log in.  The problem started after I added the line "@include common-pamkeyring" to /etc/pam.d/gdm.  I was following a walkthrough supposdely telling me a way of stopping nm-applet from asking for a password every time I log in.  Anyway, basically all I need to know is how to open gedit in recovery mode, or a way of fixing this problem.  However, I think all that needs doing is to remove that line from that file, but I don't know how to open gedit from the command line without a display.  So I guess I need to know how to open the display from the command line without having to log in.  I hope it's not anything too complicated.

Thanks a lot in advance!

---

### Post by fluffman86 on 2009-09-04
Reboot your computer, and when grub starts to load, press ESC to view your options.  The second entry should say recovery mode.  That will take you to a blue screen.  Choose "root."

Now, once you get to a command prompt, instead of "sudo gedit /etc/pam.d/gdm" type "nano /etc/pam.d/gdm"

Edit the file just like you would in gedit, and when you're done, press CTRL+X to exit, then Y to save.  

To reboot, just type "reboot now" at the prompt.

---

### Post by frogbrains on 2009-09-17
Thanks for your help, it worked!

---

