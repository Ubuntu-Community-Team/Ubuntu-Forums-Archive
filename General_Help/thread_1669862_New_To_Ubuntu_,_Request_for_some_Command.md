---
title: "New To Ubuntu , Request for some Command"
date: 2011-01-18
forum: General Help
---

### Post by FaceProblem on 2011-01-18
Im new to Ubuntu
can anyone please provide useful command for :

1)ways to enable/disable OS service(FTP/Email/Web server/Firewall/telnet/Lan file sharing)

2) basic interaction with the OS ( checking information/Open Files/Running Program)

3)Boot-loading configuration and customization

4)installation/uninstallation of programs/system patches

5)System configuration(Time setting/Date setting/User login detail change/Access right control)


thank you.

---

### Post by mastablasta on 2011-01-18
double post.

---

### Post by mastablasta on 2011-01-18
have a look here: [http://linuxcommand.org/](http://linuxcommand.org/)
a free e-book on Linux commands is available on site for download.
 
I am not sure exactly what you are trying to do but you need programmes for osme mentioned things (like webserver for exmaple)
 
Also read Ubuntu manual (more desktop oriented but still).

---

### Post by pl@yer on 2011-01-18
> **FaceProblem said:**
> Im new to Ubuntu
can anyone please provide useful command for :

1)ways to enable/disable OS service(FTP/Email/Web server/Firewall/telnet/Lan file sharing)

get used to using man pages.
stop start restart a service:
services/daemons are generaly located in /etc/init.d/
```

/etc/init.d/daemon restart

```

runlevel command will tell you what runlevel you are in.
configure whether a service will start in a certain runlevel. 
```

sysv-rc-conf

```

> 
2) basic interaction with the OS ( checking information/Open Files/Running Program)

find out if firefox is running
```

ps -ef|grep firefox

```
open files
```

fuser 
lsof 

```
> 
3)Boot-loading configuration and customization


```

apropos grub

```

> 
4)installation/uninstallation of programs/system patches

```

apt-get update
apt-get upgrade
apt-cache search progname
apt-get install progname

```

> 
5)System configuration(Time setting/Date setting/User login detail change/Access right control)

set system time, set hardware clock to system time
```

date -s datestring
hwclock -s
man ntp

```
google /etc/profile .bashrc .profile .bash_logout chmod chown usermod 
thank you.[/QUOTE]

---

