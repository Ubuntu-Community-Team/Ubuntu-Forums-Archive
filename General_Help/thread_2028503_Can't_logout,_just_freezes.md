---
title: "Can't logout, just freezes"
date: 2012-07-18
forum: General Help
---

### Post by WongFuChu on 2012-07-18
I don't know when it started happening, but I noticed it a few days ago. Whenever I try to logout, it just freezes. It stops at the black screen with the following text:

> 
could not write bytes: Broken pip
 * Starting crash report submission daemon
 * Starting clamav virus database updater freshclam
Starting GNUstep distributed object mapper: start-stop-daemon unable to stat /usr/bin/gdomap (no such file or directory)
speec-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting CUPS printing spooler/server
 * Sarting the Winbind daemon winbind
sane disabled; edit /etc/default/saned


At first, there was more text from preload and VMware, but I uninstalled it and I still get the same problem. I thought it was a kernel problem, but using different kernels (3.2.0-26-generic, 3.2.0-25-generic, and 3.2.0-23-generic) resulted in the same problem. I was able to logout once using 3.2.0-23-generic after uninstalling ccsm via ubuntu software manager in my attempt to fix the problem, but after rebooting, I'm still having problems.

---

### Post by matt_symes on 2012-07-18
Hi

Does it shutdown if you open a terminal and type
```

sudo shutdown -h now
```Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by WongFuChu on 2012-07-18
Shutting down via the terminal or even the shutdown button works. I have no problem with restarting, shutting down, sleeping, etc. (well, except for hibernating, but that's because my /home is encrypted). I just find it strange that it hangs when I logout. I can switch to a guest session when I select switch users, enter a guest session, logout of that session, and login back into my regular user session. However logging into my user account or a guest account and then logging out does not work despite the session type (gnome, unity, xbmc, cinnamon, etc.).

I think I'm just going to do a reinstall and see if that will fix my problem. :-|

---

### Post by matt_symes on 2012-07-18
Hi

If you have not reinstalled yet...

What happens if you logout from the terminal. Is it still slow ?

```
dbus-send --session --type=method_call --print-reply --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.Logout uint32:1
```

Kind regards

---

### Post by WongFuChu on 2012-07-18
Sorry, I already reinstalled =/

Luckily, I created a reinstall script to reinstall and setup most of my settings. I haven't reinstalled everything yet (because I don't remember everything that I've installed) so I'll try it and post back if I found out what I installed that caused the problem.

Thanks  for the help though! :)

---

