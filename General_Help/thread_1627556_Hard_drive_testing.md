---
title: "Hard drive testing?"
date: 2010-11-21
forum: General Help
---

### Post by chris0108 on 2010-11-21
Hi there,
   Wasnt really sure where to put this post, but im looking for some software that will test my hard drive. Iv been having a problem with the laptop crashing every now and then but its always when the hard drive light is on, just wondered if they was something to test it for bad sectors etc?

---

### Post by Hippytaff on 2010-11-21
System -> administration -> disc utility 

might be what your looking for. Also there are terminal commands to check this stuff out, but this might be easier (unless your a terminal junkie like me) :-)

Edit -> just realised your on Xubuntu not ubuntu :-s so ignore me :-) you can always check the logs though
```

cd /var/logs

ls -a

```
to list them

---

### Post by chris0108 on 2010-11-21
ls -a gives the following


chris@chris-laptop:/var/log$ ls -a
.              debug           gdm         pm-powersave.log
..             dist-upgrade    installer   pycentral.log
apparmor       dmesg           jockey.log  samba
apt            dmesg.0         kern.log    syslog
auth.log       dmesg.1.gz      lastlog     udev
boot           dmesg.2.gz      lpr.log     ufw.log
boot.log       dmesg.3.gz      mail.err    unattended-upgrades
bootstrap.log  dmesg.4.gz      mail.info   user.log
btmp           dpkg.log        mail.log    wtmp
ConsoleKit     faillog         mail.warn   Xorg.0.log
cups           fontconfig.log  messages    Xorg.0.log.old
daemon.log     fsck            news

Means nothing to me lol

---

### Post by Hippytaff on 2010-11-21
These are log files, if you open them like this
```

cat {name of a log file} | less

```you can scroll through them to find errors that will indicate the problem...you can also use the log viewer if it is easier

System -> administration -> log file viewer

this is quite useful reading
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

Edit -> did it again...Xubuntu not Ubuntu...sorry, fried brain, I think it's called event viewer in Xubuntu :-)

---

### Post by chris0108 on 2010-11-21
Thanks Hippytaff, trust me i do the same, desktop pc running ubuntu 10.10 laptop running xubuntu 10.04 nightmare at time lol

---

