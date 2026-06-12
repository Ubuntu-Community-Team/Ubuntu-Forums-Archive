---
title: "Particular USB mouse does not work for particular user"
date: 2010-09-06
forum: General Help
---

### Post by gldearman on 2010-09-06
Hi, all,

I'm having a pretty small problem, but a pretty weird one.

I created an account on my desktop for my 4-year old.  But my regular USB mouse was a bit large for his little hands.  So, I grabbed the little mouse I use for my laptop for him to use.

Problem is, the small USB mouse does not work in his account.  It can move the pointer, but clicking has unpredictable results.

The small USB mouse works fine in my account.  My regular mouse worked fine in his account, just like it works for everyone else.

His user account clearly does not have some privilege that is needed for the small mouse to work, but is not needed for the other mouse.

Anyone have any ideas where to start looking?

---

### Post by gldearman on 2010-09-06
OK, things are slightly different.

That particular user account is now having problems with *both* USB mice.

Problems are still the same, but now appear to be linked to this particular account, regardless of which mouse is used.

Thanks!

---

### Post by gldearman on 2010-09-06
Problem solved, and unrelated to user privileges.

The new mouse was a red herring; it was strictly coincidental that the problem appeared at the same time the new mouse was installed.

What had actually caused the problem was that his previous login was his first time using the Sugar desktop environment.  There is a [known bug]("http://bugs.sugarlabs.org/ticket/1544") in Sugar that it breaks a mouse setting in gconf.  No other users on my system use Sugar, so his was the only account affected.

The solution was to change a gconf setting.  I  changed /apps/metacity/general/mouse_button_modifier from "disabled" to <Super>.  Normal mouse operation restored.

Thanks to everyone who read the post!

---

