---
title: "Is X11 or GDM/KDM/XDM Handling the Login Screen in K/X/Ubuntu? What About GDM2?"
date: 2010-06-07
forum: General Help
---

### Post by OzzyFrank on 2010-06-07
OK, I really *have* tried Googling this over many, *many* hours, and I still can't make sense of it all, especially since I keep reading conflicting info.

In 9.10, the **Usplash** boot splash was replaced by **[COLOR="DarkRed"]XSplash[/COLOR]**, which is based on **X11**, and when we all realised something was up with **GDM** (when we couldn't find a way to customise the login anymore), I read it was not GDM controlling that anymore, but X11. So, the way I read it (on many different sites), XSplash in 9.10 controlled both the boot splash and the login, even though the hacks for customising the login involve commands with "**gdm**" in them.

Now, in 10.04, the short-lived XSplash has been replaced by "**[COLOR="DarkRed"]Plymouth[/COLOR]**", and I get all that... as far as the boot splash goes. What I don't understand is the login process.

There is talk of GDM2 coming out, and I've seen people asking when this will be implemented in Ubuntu, but if the move is away from GDM altogether towards a boot/login process totally based on X11, will this happen?

More importantly, what is controlling the login _now_? Is it still GDM, or is it X11 that **gdm** commands work on or something? (The hacks people used in 9.10 still work in 10.04)

Also, because I have **Xubuntu** and **Kubuntu** in the same system, and have had things like **KDM** taking over login happen after upgrades, I have to ask what is controlling the boot process and login for Ubuntu's siblings? (To me they now look almost identical, so wonder if they're all X11 based)

I'm trying to get my head around all this, so any (accurate) info would be greatly appreciated. Also any news about the future of these in Ubuntu (that isn't pure rumour) would be welcome. Many thanks in advance.

---

### Post by Chesamo on 2010-06-07
GDM is the current default display manager for Ubuntu. KDM is the default display manager for KUbuntu.

There is a display manager based purely on X11 called XDM, but it's not implemented by default in Ubuntu (it's in the repos though).

---

### Post by OzzyFrank on 2010-06-07
Yeah, when all the talk of X11 replacing GDM surfaced, I looked into XDM and realised it wasn't in Ubuntu. Actually, if I remember correctly, it was still pretty much experimental. But if the login is all still GDM, why the customisation nightmare in 9.10 (and all the talk of X11)?

I mean, even with the login applet basically neutered to the point of useless, one could still install GDM themes manually, but none of that worked when 9.10 came along. Something was obviously up, so when everyone proclaimed "It isn't GDM anymore!", it made sense, though the command-line hacks for GDM (that obviously work even now) made me scratch my head again. Hence this thread...

---

