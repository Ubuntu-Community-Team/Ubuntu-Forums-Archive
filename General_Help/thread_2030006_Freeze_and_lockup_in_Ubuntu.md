---
title: "Freeze and lockup in Ubuntu"
date: 2012-07-17
forum: General Help
---

### Post by krustenBrot on 2012-07-17
>  I could still move my mouse pointer and click on things but nothing  would happen. I had no choice but to hit the power button and restart  the computer.**+1**

I am experiencing the **exact** same problem from time to time. I already tried switching from lightdm back to gdm - didn't affect it.
I am **not** using chrome btw, firefox only and it still locks up. Sometimes I can still see my  windows (* when the login window should appear on resume from suspend*) and sometimes just my plain background image. 
I can switch to the terminal via **Ctrl+Alt+f1-6** and kill **gdm /X server **to avoid a complete restart. My opened windows, unsaved work, etc. is still gone anyway :/

Does anyone know how to specifically restart the login dialog from the locked screen? **Not** the whole window manager. I would love to know if it may be only the dialog being buggy.

//edit: I upgraded from 11.10 to 12.04 via system upgrade not a fresh install. **Irv** how about you ... maybe it is a bug that was caused during the upgrading process.

---

### Post by krustenBrot on 2012-07-17
Sorry you already answered the question about upgrading in your first post. 

Time will tell if it works if yes i will do a clean install of firefox as well. :)

---

### Post by krustenBrot on 2012-07-20
Just had another lockup.
I am attaching my syslog - sorry for the zip but the forum didn't want me to upload such a big txt file :/

---

### Post by krustenBrot on 2012-07-20
> **matt_symes said:**
> 

```

/etc/prey/config
/usr/share/prey/config
```Post back what you intend to do.

I am not entirely sure that prey is the problem though and that is why i would, personally, use option 1 first. 

Kind regards

I am not running prey, i just tried to look up the *config files*, and tried a *top | grep prey* - none of them showed me something looking like the stuff you posted. :(

---

### Post by matt_symes on 2012-07-20
Hi

@[krustenBrot]("http://ubuntuforums.org/member.php?u=1579650")

There are a whole load of reasons you may get freezes, both hardware and software.

Your freezes are being caused by a different issue than irv (assuming that it is prey that is causing irv's machine to freeze; we still have not established that).

Therefore, I have split your posts into another thread and i will PM you this link

Kind regards

---

