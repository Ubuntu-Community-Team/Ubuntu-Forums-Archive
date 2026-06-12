---
title: "can't enter x-window"
date: 2006-05-16
forum: General Help
---

### Post by gordonyb0 on 2006-05-16
I cannot enter x-window.it is said that the file '.dmrc' cannot be written.but after i use chmod to change the permission,the problem remains. I get some error infos from the file '.xsession-error':
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "cat"
/etc/gdm/Xsession: Beginning session setup...
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading simple Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.2

Can't initialize SocketServer.
Failed to initialize Panel Agent!
GTK Panel of SCIM 1.4.2

Can't initialize SocketServer.
Failed to initialize Panel Agent!
GTK Panel of SCIM 1.4.2

Can't initialize SocketServer.
Failed to initialize Panel Agent!
GTK Panel of SCIM 1.4.2

Can't initialize SocketServer.
Failed to initialize Panel Agent!
Failed to launch SCIM.
Smart Common Input Method 1.4.2

mkdtemp: private socket dir: Permission denied 
what's the solution to my problem?Pls help me

---

### Post by cskeide on 2006-05-16
Are you sure your user directory is owned by your user?

Check with:
```
cd
ls -al ..
```

If it's not, try this (replace username with your username =)):
```
sudo chown -R username.username /home/username
```

---

### Post by gordonyb0 on 2006-05-22
i've tried it,but it didn't work. 
it is said there is no -R in the usage.
but i can enter X-window as root in the recovery mode.
what else can i do to solve my problem?

---

### Post by dejitarob on 2006-05-26
[QUOTE=gordonyb0]mkdtemp: private socket dir: Permission denied[/QUOTE]Looks like you have a problem with permissions. Did you delete your /tmp dir? If so recreate it with a 'sudo mkdir /tmp'. Make sure the correct permissions are set as well with 'sudo chmod -R /tmp/ 1777'. Also, you may need to delete '/tmp/.X0-lock'.

---

### Post by gordonyb0 on 2006-06-05
Thanx a million
it does work now:mrgreen:

---

### Post by killernurd on 2006-06-20
Argh. I've followed the previously given advice for the same error, but it didn't work here.

I've been mucking around, getting things set so this machine plugs into an Active Directory structure - is there something I need to do with my PAM settings to allow GDM logins?

---

### Post by jobano on 2007-11-27
worked for me ! (my /tmp was root and 755 !!??)
thanks !

---

