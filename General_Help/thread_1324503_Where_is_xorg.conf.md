---
title: "Where is xorg.conf?"
date: 2009-11-12
forum: General Help
---

### Post by nsivin on 2009-11-12
I am using Ubuntu 9.10 on a desktop with a pivoting monitor, which I normally use in portrait mode. Setting the driver to pivot involves changing settings in /etc/X11/xorg.conf. This posed no problem in previous releases of Ubuntu from 7.04 on. The problem is that in 9.10 I can’t find xorg.conf. When I search for this file the only result is two directories, /usr/lib/xorg and /usr/lib64/xorg, but neither of these contains the file I am looking for. Any suggestions?

SETUP:
End PC Noise Workstation
4 partitions on 2 hard disks (second for backup only)
AMD Athlon dual-core 4200+ 64-bit CPU
NVIDIA GeForce 6200 Turbocache video card
ASUS A8V-E SE motherboard with 64-bit support, 3 quiet fans
2 GB DDR-400 memory

---

### Post by ricardo.gloe on 2009-11-12
KK 9.10 does not create this file automatically. You have to create it manually. 

Try:

```
Xorg -configure
```

it should generate xorg.conf, find the file and copy it to /etc/X11.

You should then be able to adjust the settings.

---

### Post by nsivin on 2009-11-14
I tried the suggestion above. “Xorg -configure” didn’t work with the initial caps; I was notified that there is no such function. 

Substituting “xorg -configure” gave me this error message:
Fatal server error: Server is already active for display 0. If this server is already running, remove /tmp/.X0-lock and start again.

I have tried deleting /tmp/.X0-lock, but that is impossible. In Nautilus I can view hidden files, but this one will not delete. In Terminal I can't view hidden files, and the command rm -f /tmp/.X0-lock doesn't do anything. (Is there a way of operating on hidden files in terminal?)

Since I have not installed, and am not running, any kind of server, I have no idea where to go from here.

---

### Post by silentrebel on 2009-12-01
I'm having a problem with the full-screen mode of my virtual box and the fix requires tampering with an inexistent xorg.conf.  
```
Xorg -configure
``` is recognised for me (with the uppercase 'x') and the first time I ran it, it gave me the 'remove /tmp/.X0-lock' message.
```
sudo rm -f /tmp/.X0-lock
``` got rid of that, after which I ran the command again...
I got this error message:
> Fatal server error:
Cannot move old log file ("var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old" 
Both of the aforementioned files exist.  I tried deleting the latter to no avail...
Any suggestions?

---

### Post by lykwydchykyn on 2009-12-01
I've always done it as:
```

X -configure

```

but you have to do this with no X server running, so first  you go to a virtual terminal (ctrl-alt-f1), login, and do:

```

sudo /etc/init.d/gdm stop

```
(If you're using kde it'd be "sudo /etc/init.d/kdm stop"; naturally, if you've got another display manager installed, you have to use whatever init script it comes with).

That will shut down your GUI (and kill your desktop session if you're logged in, so log out of your desktop first).

---

### Post by Grenage on 2009-12-01
9.10 made xorg.conf redundant, but if you create one and save it it /etc/X11/ - it will get used.

---

### Post by theozzlives on 2009-12-01
Why don't you just hold down shift (instead of esc) during boot, boot in recovery mode, go to root prompt, and then run your command?

---

### Post by NoaHall on 2009-12-01
It should be ```
 sudo Xorg -configure
```

---

