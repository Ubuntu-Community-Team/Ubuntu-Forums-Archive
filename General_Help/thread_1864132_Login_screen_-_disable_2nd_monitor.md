---
title: "Login screen - disable 2nd monitor"
date: 2011-10-18
forum: General Help
---

### Post by mcfc4eva on 2011-10-18
I have just upgraded to Ubuntu 11.10.

When you boot up a PC that is running Windows with dual monitors, only one screen loads up on the login screen and then the other switches on when logged in. How can I replicate this?

I made it work with the previous version of Ubuntu that was working, but I cannot figure out how I did it. The following code input into the terminal, successfully switches off the second monitor;

```
xandr --output DVI-0 --off
```

I want to somehow run that on the login screen when it boots up, but then after I log in, it reverts back to my user settings.

---

