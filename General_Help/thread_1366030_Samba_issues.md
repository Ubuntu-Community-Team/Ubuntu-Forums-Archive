---
title: "Samba issues"
date: 2009-12-27
forum: General Help
---

### Post by duffed on 2009-12-27
Hi,

I just install Ubuntu and for some reason the Samba service don't seem to start. I have to manualy start it after each reboot. Does anyone know why its doing that? Its a major bug for me as all my other PC are running on Windows.

Thanks

---

### Post by QrK0 on 2009-12-28
You can try
```
$ sudo chkconfig smb on
```

---

### Post by john newbuntu on 2009-12-28
Open a terminal and check if "S20samba" or "S*samba" is defined in /etc/rc3.d where * is a number.  If it is not defined, you can use the "update-rc.d" command and define it.
```
update-rc.d samba defaults
```
If this seems too much, download sysv-rc-conf using the usual apt-get install command and run it as sudo.  It has a text interface but is useful for figuring out jobs that will be started and stopped by the former System V runlevels.  Check Samba for runlevels 2 through 5.

---

### Post by duffed on 2009-12-29
Hi John,
 
Samba was already 2 to 5 levels... But I finaly fix it by reinstalling the Samba packages... probably the packages was not deploy properly on the install...
 
Thanks for your help!
 
Seb

---

