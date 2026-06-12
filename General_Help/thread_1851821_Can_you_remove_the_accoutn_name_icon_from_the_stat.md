---
title: "Can you remove the accoutn name icon from the status bar?"
date: 2011-09-29
forum: General Help
---

### Post by GumpTron on 2011-09-29
Please see screengrab :)

I would like to remove the x and the name if it is possible. Thank you :popcorn:

---

### Post by coffeecat on 2011-10-31
Bump for OP. :)

---

### Post by GumpTron on 2012-02-23
guess not :(

---

### Post by kazztan0325 on 2012-02-23
Hi GumpTron,

You can remove _your username_ on panel with **"Ubuntu Tweak"**, but cannot remove the x mark icon even if you use Ubuntu Tweak.

---

### Post by jim_deadlock on 2012-02-23
```
sudo apt-get remove indicator-me
```

---

### Post by GumpTron on 2012-02-23
thanks to both of you but can you tell me how to do this for Ubuntu 11.10? I am using the newest version and the command did not work.


Tweak did not seem to work, i did not see the option for removing icons from the tastbar/statusbar

---

### Post by jim_deadlock on 2012-02-23
You won't see it disappear immediately but it will be gone after you log out then log in again.

---

### Post by GumpTron on 2012-02-23
> **jim_deadlock said:**
> You won't see it disappear immediately but it will be gone after you log out then log in again.

nope :(


it says "virtual packages like indicator-me cant be removed"

---

### Post by jim_deadlock on 2012-02-23
Try this then:

```
sudo apt-get remove indicator-messages
```

I always remove all those indicators on new installs, I can't remember exactly which one removes that thing but it's definitely one of those indicator-xxx packages. I have 11.10 and mine is gone.

---

### Post by kazztan0325 on 2012-02-23
Hi GumpTron,

If you would like to do this on 11.10, you might want to use Ubuntu Tweak latest version (0.6.1-1~oneiric1).
See my attachment.

---

### Post by GumpTron on 2012-02-23
thank you

---

### Post by kazztan0325 on 2012-02-23
You are welcome, GumpTron!

---

