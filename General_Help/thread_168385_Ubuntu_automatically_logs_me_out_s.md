---
title: "Ubuntu automatically logs me out :s"
date: 2006-04-30
forum: General Help
---

### Post by severedspirit on 2006-04-30
After upgrading from breezy to dapper, ubuntu will not allow me to log in, i can play from a shell account but the log in screen just logs me out as soon as ive logged in. This is really confusing, hopefully one of you will no how to fix this

---

### Post by Ramses de Norre on 2006-04-30
Is there anything in ~/.xsession-errors or any error messages in /var/log/Xorg.0.log ?

---

### Post by severedspirit on 2006-04-30
hmm, didnt check that, it says something about x-session-manager lost its connection to the display :0.0
and that most likely the x server was killed

---

### Post by severedspirit on 2006-04-30
I found that this can be fixed by typing in 

sudo x-session-manager dpkg-reconfigure

however you have to login to the terminal to do this, is there a way so this works automatically when I log into gnome?

---

### Post by Kevinator on 2006-04-30
Your description of your problem doesn't make sense. I'm not sure what you mean by a "shell account". If you were being logged out then presumably you would be presented with a new login screen, and be unable to do anything other than trying to log in again.

Are you sure that you are not logged in? It sounds to me like you logged in just fine, but your X session died, thus leaving you at a command prompt. If that's the case then you can use the prompt to enter whatever commands you want. However, I would double check the command you want to use first. The one in your previous post doesn't look right to me.

---

### Post by Ramses de Norre on 2006-04-30
Can you post litteraly the contents of the files I asked? Maybe we can derive the cause of your problem out of that.

---

### Post by severedspirit on 2006-04-30
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /$
/etc/gdm/Xsession: Beginning session setup...
The application 'x-session-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

The other log file is over a thousand lines long so I havent posted it

---

