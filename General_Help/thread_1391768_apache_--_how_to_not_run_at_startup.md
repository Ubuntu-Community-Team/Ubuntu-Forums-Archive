---
title: "apache -- how to *not* run at startup"
date: 2010-01-27
forum: General Help
---

### Post by oospill on 2010-01-27
hello.  I'm wanting to install apache so I can learn php, but I don't want it running all the time.  how can I run apache only when I want to?

thanks

---

### Post by Tux+ on 2010-01-27
Stop Apache on startup:
```
$sudo update-rc.d apache remove
```

or you can install Bootup Mananer (BUM) which has a GUI interface to specify what services are started and stopped on boot:
```
$sudo apt-get install bum
```


Manually start and stop Apache when needed:
```
$sudo /etc/init.d/apache start
```
```
$sudo /etc/init.d/apache stop
```

---

### Post by Ordes on 2010-01-27
instead of remove u can also

sudo update-rc.d apache disable

sudo update-rc.d apache enable

---

### Post by warfacegod on 2010-01-27
Will using Startup Applications work?

---

### Post by mcduck on 2010-01-27
not really well, you'fd have to enter your password every time you log in (as starting/stopping apache requires root permissions while Startup Applications runn sas your normal user).

Anyway, I wouldn't bother about Apache running all the time. It really uses absolutely minimal amount of memory and pretty much zero CPU time when it's not serving any web pages. Starting/stopping it all the time won't give you any noticeable benefits, definitely not worth the trouble.

(if you are concerned about security, not resources, just configure Apache to serve to localhost only)

---

### Post by .salo on 2012-05-02
One correction here. It is necessary to use apache2 as the base name for update-rc.d. So actual commands are:

Remove:```
sudo update-rc.d apache2 remove

```Disable:```
sudo update-rc.d apache2 disable

```Enable:```
sudo update-rc.d apache2 enable

```

---

### Post by oldos2er on 2012-05-02
Old thread closed.

---

