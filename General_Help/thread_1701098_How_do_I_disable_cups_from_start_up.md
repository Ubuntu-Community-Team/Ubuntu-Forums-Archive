---
title: "How do I disable cups from start up?"
date: 2011-03-06
forum: General Help
---

### Post by highspider on 2011-03-06
This may be posted some where but I searched and searched and searched and all old post that don't work.  I'm using 10.10

why is port always opening 

system->pref..->start up
nothing for printing cups is gone 

tried```
sudo update-rc.d -f cupsd remove 
sudo update-rc.d -f cups remove
sudo update-rc.d -f cupsys remove
```and it still comes back on reboot
```
sudo sysv-rc-conf
and unchecked cups
```fliping still comes back on reboot
```

ls -l /etc/rc?.d/*ups
lrwxrwxrwx 1 root root 14 2011-03-07 17:20 /etc/rc1.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 14 2011-03-07 17:32 /etc/rc2.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 14 2011-03-07 17:32 /etc/rc3.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 14 2011-03-07 17:32 /etc/rc4.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 14 2011-03-07 17:32 /etc/rc5.d/K80cups -> ../init.d/cups

sudo rm /etc/rc?.d/*ups

ls -l /etc/rc?.d/*ups
ls: cannot access /etc/rc?.d/*ups: No such file or directory

sudo update-rc.d -f K80cups remove

```

```

sudo netstat -nlupt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1058/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN   
----skipping-----

```

---

### Post by highspider on 2011-03-07
> **gmargo said:**
> in 10.10 maverick, the **upstart** system starts system daemons.  To disable **cups**, edit the **/etc/init/cups.conf** file and comment out these three lines for "start on":
```

start on (filesystem
          and (started dbus or runlevel [2345])
          and stopped udevtrigger)

```


this worked

---

