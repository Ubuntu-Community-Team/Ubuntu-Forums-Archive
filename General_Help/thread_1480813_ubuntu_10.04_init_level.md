---
title: "ubuntu 10.04 init level"
date: 2010-05-11
forum: General Help
---

### Post by tech78i on 2010-05-11
How do I go about changing the init level to 3 on ubuntu 10.04?!? Where is the old inittab file? Do I need to make? I want to boot to a console. Thank you all!

Tech78i

---

### Post by pytheas22 on 2010-05-12
Ubuntu doesn't really use init anymore; it uses [Upstart]("http://upstart.ubuntu.com/") instead.  But the last time I checked, the old init calls were still supported.  Are you not able to change to runlevel 3 by typing:
```

sudo init 3
```

---

### Post by tech78i on 2010-05-12
:) Yes, but I would like to do this during the boot process. Is their a way? i have created an inittab file and put in the one liner that use to work in previous versions. But it still boots to GUI. Thank you!
 
Tech78i

---

### Post by tech78i on 2010-05-12
Do the following to modify the upstart runlevel to 3. Problem solved!
 
Tech78i:P
 
in **[COLOR=#151515]/etc/init/rc-sysinit.conf[/COLOR]**:
env DEFAULT_RUNLEVEL=3
 
in **[COLOR=#151515]/etc/init/gdm.conf[/COLOR]**:
start on (filesystem
and started hal
and tty-device-added KERNEL=tty7
and (graphics-device-added or stopped udevtrigger)
and runlevel [!3])
stop on runlevel [016]

---

