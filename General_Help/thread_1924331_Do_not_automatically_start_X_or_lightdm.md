---
title: "Do not automatically start X or lightdm"
date: 2012-02-12
forum: General Help
---

### Post by Rafterman414 on 2012-02-12
Hello everyone I am trying to find out how to make it so by default when I boot into Ubuntu I go into text only mode and then if I need to start X I'll do that later. I tried to do a search on this but all I am finding is posts about people who cannot get X or gdm or lightdm to start. 
I have tried to disable it with the following command:
```
sudo update-rc.d -f lightdm remove
```With no luck so far.

The reason why I would like to do this is because most of the time I just use X11 Forwarding over SSH. 

I am sure a solution to this has been posted somewhere but like I said all I am finding is troubleshooting for people who can't get to the GUI at all. Thanks for the support!

---

### Post by Rafterman414 on 2012-02-12
Ok so I think I might be on the right track by editing /etc/init/lightdm.conf in particular I am looking at this section:
```
start on ((filesystem
           and runlevel [!06]
           and started dbus
           and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                or stopped udev-fallback-graphics))
          or runlevel PREVLEVEL=S)

stop on runlevel [016]

```

I guess I just need to modify that script for the start section to have it not start on any run levels.

---

### Post by Rafterman414 on 2012-02-12
Ok well that made it so X does not start by removing everything from the start on section but when I login and do startx I get a very minimal looking GUI without the unity bar, pretty much just icons on the desktop I tried to do sudo service start lightdm but it said nothing found. The end result that I would like to see from this is at boot default of text only console, then hopefully enter one command to restore the desktop interface if I am working on the actual machine.

---

### Post by ajgreeny on 2012-02-12
```
sudo service lightdm start
``` may work.  I think you got it back to front.

---

### Post by Rafterman414 on 2012-02-12
> **ajgreeny said:**
> ```
sudo service lightdm start
``` may work.  I think you got it back to front.

That did the trick, everything is working just like it should now! Thanks, I feel like an idiot for mixing up that command.

---

