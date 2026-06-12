---
title: "How do i stop samba from starting at boot?"
date: 2009-11-30
forum: General Help
---

### Post by chrisbay90 on 2009-11-30
How do i stop samba from starting at boot? I rarely need to share a file through samba, and when I do I know about it. So i can just run /etc/init.d/samba start.

For that matter how do alter what scripts run from /etc/init.d or elsewhere or even add my own stuff to run. A link or pointer in the right direction would be greatly appreciated. I'v been searching in vein for quite some time.

---

### Post by Leppie on 2009-11-30
You could install sysv-rc-conf:
```
$sudo apt-get install sysv-rc-conf
```

Run it like this:
```
$sudo sysv-rc-conf
```
You can select which daemons to start for all runlevels

---

### Post by Giblet5 on 2009-11-30
Take a look at the linked files in /etc/rc2.d

Run ```
who -r
```

It shows you're at runlevel 2, right? So the scripts linked to the rc2.d directory will run in the same order as output by ```
ls -1 /etc/rc2.d
```

Remove the link to /etc/init.d/samba and you'll stop it from starting with the init state change to runlevel 2.

You'll have to stop it manually for this run though.

---

### Post by sanemanmad on 2009-11-30
update-rc.d will help you manage what RC level to run services.

```
michael@alice:~$ update-rc.d
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force

```

---

### Post by chrisbay90 on 2009-12-01
Thanks Leppie sysv-rc-conf worked perfectly. Very easy to.

Also thanks Giblet5 and sanemanmad for the starter info on how these scripts work. This should really get me going in the right direction in understanding how everything works. I'm somewhat new to linux and the ability to alter your system and see how everything is done is such breath of fresh air coming from you know what...

---

