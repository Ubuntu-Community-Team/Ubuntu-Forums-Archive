---
title: "Add command on boot"
date: 2010-06-30
forum: General Help
---

### Post by Joel.S123 on 2010-06-30
Hi! I need to add a root command before x11 loads. How do i do that?

---

### Post by CannibalZerg on 2010-06-30
Put your commands without *sudo* to /etc/rc.local before the "exit 0" line.

---

### Post by Joel.S123 on 2010-06-30
Thanks for the quick reply, but I don't think that is what I'm looking for because, according to [https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto), the script is run after x11 has been started. X11 is a system service, right?

---

### Post by iponeverything on 2010-06-30
I think you might be looking for the .xinitrc.

do a:
```

man xinit
```

and google around for xinitrc examples.

---

### Post by CannibalZerg on 2010-06-30
Create /etc/init/myscript.conf file with something like:
```

description "Starts custom scripts"

start on startup
#start on local-filesystem
#start on runlevel [5]

task
script
   #put your command(s) here
end script

```I don't know what are you trying to do within your custom scripts, so choose correct "start on" option.
Maybe you will need to change gdm.conf to guarantee, that myscript will run before gdm. In this case you should change "start on" option in gdm.conf to:
```

start on (filesystem
          and started dbus
          **and started myscript**
          .........

```
Original thread: [http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10](http://superuser.com/questions/133595/running-a-script-on-startup-before-x-starts-in-ubuntu-9-10)

P.S. AFAIK xinitrc ignored when using GDM

---

### Post by Joel.S123 on 2010-06-30
I need to copy a correct xorg.conf to /etc/X11 before it gets read since my system occasionally overwrites it when i shutdown.

Does ```
start on local-filesystem
``` mean once the system partition is mounted?

---

### Post by CannibalZerg on 2010-06-30
I think so, but I can't find detailed upstart documentation.

IMHO much easier to change xorg.conf permissions and make it read-only.

---

### Post by dino99 on 2010-06-30
actual kernel deals with X, so no need of xorg.conf

sudo rm -f /etc/X11/xorg.conf

if you need a special command be ran early, put it on the boot line


sudo gedit /etc/default/grub

---

### Post by Joel.S123 on 2010-06-30
> **CannibalZerg said:**
> I think so, but I can't find detailed upstart documentation.

IMHO much easier to change xorg.conf permissions and make it read-only.

I feel so stupid right now :p That probably solved it.

---

