---
title: "Startup manager question"
date: 2011-07-02
forum: General Help
---

### Post by forrestcupp on 2011-07-02
I read that at one time, startup manager didn't work well with grub2 and that it could bork your system. Does anyone know if they've gotten it to the point where it works with grub2?

If not, are there any alternatives to modify grub2 with a gui?

---

### Post by grahammechanical on 2011-07-02
Grub Customizer gets my vote.

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

regards.

---

### Post by aura7 on 2011-07-02
Use Startup-Manager available under System->Administration in Ubuntu most versions.

---

### Post by Rubi1200 on 2011-07-02
> **grahammechanical said:**
> Grub Customizer gets my vote.

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

regards.
+1 for Grub Customizer; well worth checking out the link there.

---

### Post by forrestcupp on 2011-07-02
Thanks guys. I didn't notice Startup-Manager is preinstalled. I guess they wouldn't include something that doesn't work, would they?

---

### Post by drs305 on 2011-07-02
> **forrestcupp said:**
> Thanks guys. I didn't notice Startup-Manager is preinstalled. I guess they wouldn't include something that doesn't work, would they?

StartUp-Manager can do a few of the basics in Grub 2 but doesn't have nearly the versatility of Grub Customizer. For setting timeouts or the default OS it works fine with at least Grub 2 up through Maverick [noparse] (Grub 1.98)[/noparse].

Grub 1.99RC was introduced in Ubuntu with Natty, and it introduces 'submenus'. I don't know if StartUp-Manager works well with submenus...

---

### Post by forrestcupp on 2011-07-02
> **drs305 said:**
> StartUp-Manager can do a few of the basics in Grub 2 but doesn't have nearly the versatility of Grub Customizer. For setting timeouts or the default OS it works fine with at least Grub 2 up through Maverick [noparse] (Grub 1.98)[/noparse].

Grub 1.99RC was introduced in Ubuntu with Natty, and it introduces 'submenus'. I don't know if StartUp-Manager works well with submenus...

Yeah, I just used Startup-Manager to set the default OS and timeout, but it's seriously lacking. You can't even change the order of things. Oh well, it got done what I was mainly wanting.

I'll have to check out Grub Customizer. Thanks everyone.

---

