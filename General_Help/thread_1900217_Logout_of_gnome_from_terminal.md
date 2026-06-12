---
title: "Logout of gnome from terminal"
date: 2011-12-25
forum: General Help
---

### Post by 5heba on 2011-12-25
Is there a way to logout the current gnome/X session from a terminal/bash session (tty1-tty6)?
I try:
```
sudo gnome-session-save --logout

or

sudo gnome-session-save --kill --silent
```only to get "** (gnome-session-save:3002): WARNING**: Unable to start: Cannot open display"


Running Ubuntu 10.04 with gnome 2.30.2
all up to date

---

### Post by matt_symes on 2011-12-25
Hi

Does it work if you export the display variable ?

```
DISPLAY=:0 sudo gnome-session-save --logout
```

Kind regards

---

### Post by hhh on 2011-12-25
```
dbus-send --session --type=method_call --print-reply --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.Logout uint32:1
```

Since that's rather long, I keep that as a script named logout in /usr/local/bin and call it from the Run dialog. If you wanted to run the script from a terminal, name it something else like leave.

An alternative is pkill -KILL -u hhh (replace hhh with your user name)...
[http://www.cyberciti.biz/faq/linux-logout-user-howto/](http://www.cyberciti.biz/faq/linux-logout-user-howto/)
[http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html](http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html)

---

### Post by kerry_s on 2011-12-25
sudo service gdm stop

---

### Post by 5heba on 2011-12-25
> **matt_symes said:**
> 

Does it work if you export the display variable ?

```
DISPLAY=:0 sudo gnome-session-save --logout
```

No, didn't work.  Not really sure what the DISPLAY variable does.


I did get this to work however:
```
sudo service gdm restart
```Then saved it as an alias by adding
```
alias gnome-logout='sudo service gdm restart'
```to /home/**username**/.profile

---

