---
title: "Recovery Mode to Normal Mode???"
date: 2010-12-07
forum: General Help
---

### Post by savvas999 on 2010-12-07
hello guys, 
i installed ubuntu today so im a begginer. I accidentally chose the "recovery mode" and now i dont know what to do. What commands i have to enter to go back to normal ubuntu mode with graphic etc?

Thanks a lot

---

### Post by wojox on 2010-12-07
Type

```
reboot
```

---

### Post by mcduck on 2010-12-07
"reboot" :)

That will reboot the machine and you'll be able to select the normal mode from the boot menu.

---

### Post by savvas999 on 2010-12-07
:oops::oops::oops: oh guys.... haha, thanks a lot. I'll give it a try... thanks again

---

### Post by savvas999 on 2010-12-07
i tried to type reboot but said that "need to be root"
then i typed "sudo reboot" and then the machine is rebooted.

So a box appeared with my username inside, and i had to enter a pass. There aren't any other options (to choose normal mode), just my username, and then you enter a pass and log in. **Any other suggestions please?**

Sorry for my "stupid" topic, hope to find help...

---

### Post by savvas999 on 2010-12-07
any help? :( 

(sorry for the posts, when i find a solution you can delete all my posts.)

---

### Post by wojox on 2010-12-07
That's weird. Recovery mode usually drops you to a root shell.

What do you want to do? Login automatically?

---

### Post by savvas999 on 2010-12-07
As i said before, i just want to go to the normal mode of ubuntu. I accidentally chose the "recovery mode" and i have no idea what to do :(
I tried to enter "reboot", but nothing happens, it said that "need to be root", so i enter "sudo reboot". My laptop is rebooted and a box appeared. Inside the box are my username and password (nothing else). I type my pass and then a small window appear left-above to the screen.

---

### Post by wojox on 2010-12-07
Sounds like your in x-term.

When you get to GDM look at the bottom for sessions and choose Gnome. You may have to click your name first. ;)

---

### Post by savvas999 on 2010-12-07
so i choose gnome, click my name and then type "reboot"? ;)
Thanks, I'll give it a try...

---

### Post by mcduck on 2010-12-07
> **savvas999 said:**
> i tried to type reboot but said that "need to be root"
then i typed "sudo reboot" and then the machine is rebooted.

So a box appeared with my username inside, and i had to enter a pass. There aren't any other options (to choose normal mode), just my username, and then you enter a pass and log in. **Any other suggestions please?**

Sorry for my "stupid" topic, hope to find help...

In that case you are not in the recovery mode (which would be a pure command-line interface, and would log you in as root automatically).

If you get the graphical login screen, there's a "session" button in the bottom of the screen. Just click that and select "Ubuntu Desktop Edition". (the option only appears after you have typed in your user name, but before you enter the password.)

If that doesn't get you into normal Gnome desktop there's probably something wrong with your graphics drivers.

(If you have ended in the Recovery Console, which is selected from the login screen and gives you an xterm window, you don't need to reboot the machine. Simply running the "*exit*" command will get you back to the login screen.)

---

