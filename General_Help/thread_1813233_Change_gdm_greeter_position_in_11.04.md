---
title: "Change gdm greeter position in 11.04"
date: 2011-07-27
forum: General Help
---

### Post by harden@gsu.edu on 2011-07-27
I have a dual monitor setup using TwinView running an up-to-date Ubuntu 11.04 amd64.  The GDM (login) greeter is displayed in the center of the screen, and thus, one half of the greeter is on the left monitor and the other half is on the right monitor.   I've been trying to find away to move the greeter to only one monitor. I've searched Google and the forums for an answer. 

Here's what I've tried:
1)  gmdsetup => does not have an option to position the greeter
2)  gconf-editor => does not have an option to position the greeter
3) ubuntu-tweak => does not have an option to position the greeter
4) Tried these settings in /etc/gdm/custom.conf,  /etc/gdm/gdm.conf,   /etc/gdm/gdm.conf-custom, /etc/X11/gdm/gdm.conf:

```

[greeter]
SetPosition=true
PositionX=200
PositionY=300

```5) Mucked around with  /usr/share/gconf/schemas/gdm-simple-greeter.schemas , /usr/share/gdm/gdm-greeter-login-window.ui, /var/lib/dpkg/info/gdm.conffiles

Any other things to try?

Thanks,
Don

---

### Post by Slim Odds on 2011-07-27
Did you restart GDM after you changed the config files?

---

### Post by harden@gsu.edu on 2011-07-27
Yes, I restarted gdm after each change.
      $> service gdm restart

---

### Post by Slim Odds on 2011-07-27
> **harden@gsu.edu said:**
> Yes, I restarted gdm after each change.
      $> service gdm restart

try: ```
sudo service gdm restart
```

---

### Post by harden@gsu.edu on 2011-07-28
I was root.  When I am doing a lot of sysadmin stuff I just become root with  ```
sudo su -
``` A lot easier than typing sudo in front of each command.  Also, just for ducks, I  even rebooted a few times.  

In spite of what the docs say, it seems that /etc/gdm/custom.conf is not being parsed.       


Don

---

