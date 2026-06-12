---
title: "Boot into text mode in 9.10"
date: 2010-04-16
forum: General Help
---

### Post by smay84 on 2010-04-16
Hi

I'm trying to setup a Ubuntu FTP virtual server.  The host computer is more than able to run the virtual server with X Windows but to save resources i'd like to be able to switch it off and on.  I know server edition is text mode by default but i would like the option of being able to load the GUI if i needed it, then switch it off again when i'm done.

How would do i do that.  I've trawled google for hours with no luck.  I found some stuff about moving or deleting S30gdm file but i can't find it.

I know this sounds somewhat pointless but its just one of those things i'd like to know how to do.

Si

---

### Post by nothingspecial on 2010-04-16
Why not just stop gdm

```
sudo service gdm stop
```

---

### Post by smay84 on 2010-04-16
it says command not found:

sudo service gdm stop
sudo: service: command not found

---

### Post by sisco311 on 2010-04-16
```
sudo initctl stop gdm
```
```
sudo initctl start gdm
```

To boot directly into text mode, edit the /etc/default/grub file & replace the **quiet splash** kernel parameters with **text**:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**text**"
GRUB_CMDLINE_LINUX=""
...
```
then run:
```
sudo update-grub
```

---

### Post by smay84 on 2010-04-16
it now says in 8.04

```
initctl: Uknown job: gdm
```

and in 9.10 it just crashes.

both a clean installs with nothing done to them

..really amazed at how fast people get back to you on the Ubuntu forums by the way.

---

### Post by sisco311 on 2010-04-16
in 8.04 you have tuo run:
```
sudo /etc/init.d/gdm stop
```

---

### Post by smay84 on 2010-04-16
i tried sudo /etc/init.d/gdm stop and it just hangs after:

```
* Running local boot scripts (/etc/rc.local)    [ OK ]
```

One thing that just came to mind is that i am running this in VirtualBox and have installed the Guest Additions.

---

### Post by tilixibr on 2010-05-10
I have the exact same issue. I'm trying to install my NVidia graphics driver, and it tells me to install in text mode. Ctrl-Alt-F1 doesnt work on VMWare. Does anyone have any ideas?:???:

---

### Post by pseudov on 2010-06-08
You can't find S30gdm?  Since your default runlevel is 2, you would want change it in /etc/rc2.d .  Don't delete it, rename it to K30gdm.  More info is in the readme file in the same directory.  Alternatively, you could just run:

```

sudo update-rc.d -f gdm remove

```Which effectively accomplishes the same thing, but for all runlevels.


Edit:  When/if you want to change it back, just run ```
sudo update-rc.d -f gdm defaults
```

---

