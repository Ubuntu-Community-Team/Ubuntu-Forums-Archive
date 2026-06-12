---
title: "Trying to boot to shell"
date: 2009-12-31
forum: General Help
---

### Post by TaeBoX on 2009-12-31
I have searched around and I can't seem to find any way to do this. It was very simple in Fedora, all I needed was a 3 on my kernel line in grub. Does anyone know how to do it in Ubuntu?

Also, how do I get a daemon to run at the lower run level? This was also easily accomplished in Fedora with chkconfig.

Specifically what I want is sabnzbdplus, samba, and ssh running on a headless machine that does not boot to a gui.

---

### Post by dcstar on 2009-12-31
> **TaeBoX said:**
> I have searched around and I can't seem to find any way to do this. It was very simple in Fedora, all I needed was a 3 on my kernel line in grub. Does anyone know how to do it in Ubuntu?

Also, how do I get a daemon to run at the lower run level? This was also easily accomplished in Fedora with chkconfig.

Specifically what I want is sabnzbdplus, samba, and ssh running on a headless machine that does not boot to a gui.

Either install the Server version or remove the ubuntu-desktop package and all the things associated with it.

---

### Post by TaeBoX on 2009-12-31
> **dcstar said:**
> Either install the Server version or remove the ubuntu-desktop package and all the things associated with it.

I was hoping for something less permanent. I guess server would make the most sense. Does server default to non-gui operation?

---

### Post by Leppie on 2009-12-31
> **TaeBoX said:**
> I was hoping for something less permanent. I guess server would make the most sense. Does server default to non-gui operation?

you could try installing tools like sysv-rc-conf, with which you would be able to configure what daemons to start for each runlevel. not sure if it works with upstart and the daemons you listed as well, but may be worth trying.

---

### Post by dcstar on 2009-12-31
> **TaeBoX said:**
> I was hoping for something less permanent. I guess server would make the most sense. Does server default to non-gui operation?

You could manually take out the GDM startup, then you could start it from a terminal if necessary.

I have seen this answered in detail previously, do a forum search.

---

### Post by TaeBoX on 2010-01-01
> **dcstar said:**
> You could manually take out the GDM startup, then you could start it from a terminal if necessary.

I have seen this answered in detail previously, do a forum search.

Thank you. This should do the trick.

Also for anyone wondering, SABnzbd+ is the premier NZB downloader around. If you haven't tried it yet, do. 

Thanks to all, cheers.

---

### Post by Leppie on 2010-01-01
if you edit /etc/init/gdm.conf, you should be able to set if it starts or not at boot.
if you change the first section to something like this:
```
start on (runlevel [345]
	  and filesystem
	  and started hal
	  and tty-device-added KERNEL=tty7
	  and (graphics-device-added or stopped udevtrigger))
stop on runlevel [016]

```
it should not start when entering runlevel 2 & 1, i have not tested it though.

---

### Post by TaeBoX on 2010-01-01
> **Leppie said:**
> if you edit /etc/init/gdm.conf, you should be able to set if it starts or not at boot.
if you change the first section to something like this:
```
start on (runlevel [345]
	  and filesystem
	  and started hal
	  and tty-device-added KERNEL=tty7
	  and (graphics-device-added or stopped udevtrigger))
stop on runlevel [016]

```
it should not start when entering runlevel 2 & 1, i have not tested it though.
Thanks for the tip. I just commented out the start on and following "and" lines. That seems to have worked well.

---

### Post by Leppie on 2010-01-01
> **TaeBoX said:**
> Thanks for the tip. I just commented out the start on and following "and" lines. That seems to have worked well.

ah, it wasn't clear to me you wanted to disable gdm autostarting in all runlevels.

---

### Post by TaeBoX on 2010-01-02
Having removed those lines, it does just what I wanted it to. You only have to modify one file to get SABnzbd+ to run at start (just to choose the user it runs under). Now when I want the gui, I just ```
$ startx
```

Thanks for the help.

---

### Post by Leppie on 2010-01-02
> **TaeBoX said:**
> Having removed those lines, it does just what I wanted it to. You only have to modify one file to get SABnzbd+ to run at start (just to choose the user it runs under). Now when I want the gui, I just ```
$ startx
```

Thanks for the help.

you're welcome, glad it's working as you want it to ;)

---

