---
title: "login: pressing first letter of my password causes reboot"
date: 2011-03-30
forum: General Help
---

### Post by sanderj on 2011-03-30
Hi,

A very curious problem:

Ubuntu boots normally, and the login screen appears. When I press the 'g'-keybutton (the first letter op my password), the system complete reboots.

Pressing the 'q' does not cause a reboot.

Filling out my password using the onscreen keyboard goes OK.

After logging in (using the onscreen keyboard method), I can just press the G without problems, and the system is stable.

Any ideas what's going on?

---

### Post by Krytarik on 2011-03-30
That's is indeed very curious!

After checking some possible culprits, my best bet right now is to re-install "gdm":
```
sudo apt-get install --reinstall gdm
```
Then reboot, and see again.

Greetings.

---

### Post by sanderj on 2011-04-01
> **Krytarik said:**
> That's is indeed very curious!

After checking some possible culprits, my best bet right now is to re-install "gdm":
```
sudo apt-get install --reinstall gdm
```
Then reboot, and see again.

Greetings.

I did that, rebooted, and ... I can login withou problems ... fascinating!

FWIW: the on-screen keyboard is still there. So strictly speaking (spoken?), I have to disable that to really test it.

Thanks!

---

### Post by Krytarik on 2011-04-01
> **sanderj said:**
> 
FWIW: the on-screen keyboard is still there. So strictly speaking, I have to disable that to really test it.

But you know how to do that, right? Should be possible through the lower right panel item, but if it's not, you can simply run this command:
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_keyboard_enabled --type bool --set false
```

---

