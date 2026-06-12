---
title: "How to make a hidden account in Ubuntu?"
date: 2010-10-12
forum: General Help
---

### Post by silkworm2.5 on 2010-10-12
Hi.
I wondering how I can make an account in Ubuntu that doesn't appear on the log-in screen, but needs to be typed in in the "Other" Box. How do I do that?

---

### Post by mikewhatever on 2010-10-12
Run 'gconf-editor' in Terminal, navigate to /apps/gdm/simple-greeter and tick the 'hide_user_list' box.

---

### Post by silkworm2.5 on 2010-10-12
Thanks Mike
But it's a little different in 10.10 because the closest to that is Disable_User_List. same thing though. thanks!

---

### Post by silkworm2.5 on 2010-10-12
hey, sorry but it didn't work. the list is still there...

---

### Post by mikewhatever on 2010-10-13
Oh well, but it looked promising.

---

