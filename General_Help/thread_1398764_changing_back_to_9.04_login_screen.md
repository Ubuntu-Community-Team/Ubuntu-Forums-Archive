---
title: "changing back to 9.04 login screen"
date: 2010-02-04
forum: General Help
---

### Post by litspliff on 2010-02-04
i need a login screen that doesn't list all the users, rather the user must type in his name. i knew how to change this in 9.04, but the option seems to be removed in 9.10. i was hoping someone could point me in the right direction.

thx,
=j

---

### Post by fisheater on 2010-02-04
This works well (at least on my setup). Have a look: 

[HTML]http://www.ubuntugeek.com/how-to-remove-hide-users-list-at-login-screen-in-ubuntu-9-10-karmic.html[/HTML]

---

### Post by litspliff on 2010-02-05
[http://www.ubuntugeek.com/how-to-remove-hide-users-list-at-login-screen-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-remove-hide-users-list-at-login-screen-in-ubuntu-9-10-karmic.html)
MUCH THANX, FISH

first i'd like to make a general complaint about ubuntu taking a step backwards in some respects with the newer version of this distro. why would you remove this option from being accessable from the gnome desktop? i could go on for several paragraphs, but i already did, and nobody replied to the thread, so i guess i'm in the minority of opinion. moving on....

i used the **"2nd Method"**

1. Logout of your current session and return to the GDM
 2. Switch to the tty command line prompt using Ctrl-Alt-F1
 3. Login using your normal login/password
 4. at the command line prompt type: export DISPLAY=:0.0
 5. then type: sudo -u gdm gconf-editor
 6. Switch back to the gdm screen using ALT-F7
 7. Then navigate to /apps/gdm/simple-greeter and tick disable user list
 8. Restart gdm
  sudo /etc/init.d/gdm restart

i recommend the second method because the settings tool (which i previously was unaware of) is loaded with all kinds of goodies. some of these could do some real damage, so be careful when exploring. settings are saved in real time, so if you don't know what a setting does, make sure you do some research before clicking on stuff.....or for fun you could just change a bunch of random stuff and see if the thing still works!

---

### Post by litspliff on 2010-02-05
another question...
when i did the upgrade on my previous system from 9.04 --> 9.10 i still had my original 9.04 login screen. is it possible to install this on karmic? that would be great because the grey/brown theme is seriously cramping my style, and the 9.04 login screen was quite nice. 

 i'm off to change my xsplash screen. 
i'm tired of the feces spotlight everytime i boot.


p.s.
don't take this like i'm down on ubuntu...it's the *only* distro for my laptop, and though i get frustrated with this or that, it's the best thing out there that i've found, and it sure beats paying for crappy software.

---

