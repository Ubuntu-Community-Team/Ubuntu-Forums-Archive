---
title: "Empty Desktop - Help Please"
date: 2011-05-18
forum: General Help
---

### Post by BennieBlount on 2011-05-18
I installed 11.04. Also installed CompizConfig Settings Manager in order to remove Unity desktop and go back to the classic gnome desktop. In CompizConfig Settings Manager I unchecked "enable Unity plugin." The moment I unchecked it everything disappeared from the desktop. Now I have a blank desktop with nothing on it. 

I want to use the classic gnome desktop. I understand now that I could have chosen the gnome desktop when I logged on, but I have automatic login, so that won't work for me now.

Is there a way to fix my desktop without re-installing 11.04?

Thanks,
Bennie

---

### Post by BennieBlount on 2011-05-18
OK, re-install.

---

### Post by coffeecat on 2011-05-18
> **BennieBlount said:**
> OK, re-install.

You gave up after only 11 minutes?

If you want to know how you can disable automatic login from a blank desktop, post back. I have a possible solution.

---

### Post by mikewhatever on 2011-05-18
That was fast. Anyway, next time you decide to break Unity, hit ctrl+alt+t to bring up a terminal window and run 'unity --reset' to reset Unity to the default state.
To logout, hit ctrl+alt+f1, login and run 'sudo service gdm restart'.
That should take you to the login screen where you can select the session to use.

---

