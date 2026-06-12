---
title: "Cannot login after adding a user"
date: 2011-03-27
forum: General Help
---

### Post by RandomSF on 2011-03-27
Running 10.10. Had one user and now wanted to add a second user.
Added the user and a password, disabled auto-logon and set system to show the list of users. Upon reboot, I get the list of two users and 'Other...'. Clicking any of this just loops back to the same screen. I am now unable to log on to the machine at all. 

What is a way to reset this so I can log in?

---

### Post by 3Miro on 2011-03-27
Have you tried holding the shift on reboot and then selecting "failsafe" mode.

---

### Post by Krytarik on 2011-03-27
Right now I don't know why it behaves that way, but in order to quickly enable you to at least autologin like before:

When you are at the login screen
- press Ctrl+Alt+F1 to switch to a console
- login there
- modify the GDM config manually:
```
sudo nano /etc/gdm/custom.conf
```- put it similar to this:```

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=krytarik
AutomaticLogin=krytarik
TimedLoginDelay=10
DefaultSession=gnome
```- press Ctrl+O and confirm with Enter/Return to save it
- press Ctrl+X to quit
- restart GDM:
```
sudo service gdm restart
```

---

### Post by RandomSF on 2011-03-27
Thanks, Krytarik, your solution has me back in the system.

I'll work out the rest from here.

---

