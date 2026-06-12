---
title: "System -&gt; Administration -&gt; [...] asking for wrong user's password"
date: 2011-09-21
forum: General Help
---

### Post by thimble on 2011-09-21
I have a strange problem. When I installed Ubuntu, the first user I created was userX, who has admin privileges.

Then I created my own username, userY, who also has admin privileges.

However, when I log into Gnome as userY and try to change some settings in the System -> Administration menu, it asks for userX's password, not my own userY password. Typing in userX's password succeeds in changing the settings.

How do I get the graphical password thing to ask for my own userY password, and not userX's?

Note: sudo works fine. sudo correctly asks for my own password and not userX's.

Thanks for your help.

---

### Post by dcstar on 2011-09-22
> **thimble said:**
> I have a strange problem. When I installed Ubuntu, the first user I created was userX, who has admin privileges.

Then I created my own username, userY, who also has admin privileges.

However, when I log into Gnome as userY and try to change some settings in the System -> Administration menu, it asks for userX's password, not my own userY password. Typing in userX's password succeeds in changing the settings.
.........

Is the second account a member of the **admin** group?

---

### Post by thimble on 2011-09-22
No, userY wasn't a member of the admin group. After adding userY to the admin group, the behavior is correct.

I guess you have to be in the admin group for the graphical sudo program to work correctly?

Thanks so much for your help!

---

