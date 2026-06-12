---
title: "Ubuntu 10.04: Compiz Reflection HELP"
date: 2011-03-10
forum: General Help
---

### Post by SexySara on 2011-03-10
I enabled Compiz Reflection and now I can't seem to get to my desktop. It logs me out and brings me to the log in screen and when I log back in it starts all over again and I have to log back in... it NEVER stops. I only set up one account on my computer. How do I recover from this without having to reformat? I am using my live disc right now. This happened last night and I didn't know what I pushed and I saved all my files then reformatted, but I am not gonna do that a second time. Help please!

---

### Post by ~Plue on 2011-03-10
clearing the config files may help
at the login screen, press ctrl+alt+F1 and enter your log in username/password

at the prompt, enter
```
mv /home/$USER/.config/compiz/  /home/$USER/.config/compiz.backup/

```then press alt+ctrl+F7/F8 to get back to the normal login screen and try again

---

### Post by SexySara on 2011-03-10
Okay I will try that and report back...  

[SIZE=2]**EDIT**[/SIZE] 
You my friend are a hero! To think, this happened to me last night and I completely backed up all my files and just reinstalled from the live disc. WOW! I can't wait to help someone else that has the same issue I had! Thank you soooo much!

---

### Post by Krytarik on 2011-03-10
You don't need to do that!

Just login to "Failsafe GNOME" session, choose it at the bottom after you clicked/entered your username. Then disable that plugin or change its settings.

---

### Post by ~Plue on 2011-03-10
> **Krytarik said:**
> You don't need to do that!

Just login to "Failsafe GNOME" session, choose it at the bottom after you clicked/entered your username. Then disable that plugin or change its settings.
apologies
i haven't used gdm/gnome for a while and forgot that option existed

---

### Post by SexySara on 2011-03-10
No worries... it worked out after all. I was just messing with some settings in compiz so I don't mind resetting what I had. I am NOT messing with the reflection thing anymore. Next time I will try the failsafe one and see how that works. Thank you both very much!

---

### Post by Krytarik on 2011-03-10
> **~Plue said:**
> apologies
i haven't used gdm/gnome for a while and forgot that option existed
You could also do a *full* "recovery mode" boot, chosen at the boot menu.

---

