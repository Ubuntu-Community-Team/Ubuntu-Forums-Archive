---
title: "bizzare google earth problem"
date: 2006-06-23
forum: General Help
---

### Post by imaca on 2006-06-23
1. Added google earth to menu and launcher panel.
2. Tried to launch using menu and launcher panel - all OK.
3. Try again 3 days later - doesn't work
4. Cut and paste launch command from menu into terminal - google launches!

These kind of bizzare bugs are starting to erode my confidence in Ubuntu.:confused:

---

### Post by JARofHERB on 2006-06-23
Are you running gnome?

---

### Post by imaca on 2006-06-23
Yep.
The only thing I have done since it broke is install updates.

---

### Post by JARofHERB on 2006-06-23
Yep, gnome for some reason is doing this to random apps that i pin to the launcher panel also. Ive noticed this with 4 diffrent programs now..Intresting.

---

### Post by imaca on 2006-06-24
I figured it out -
if I set menu item to "run in terminal" it comes up and asks for password, then Googleearth runs.
When I first used it I must have just used sudo command previously, this seems to give sudo privileges for a little while after, so menu icon worked.
(I wondered why it never asked for the password)

---

### Post by mgmiller on 2006-06-24
This drove me nuts for a bit also.  It happened because I installed googleearth as root.  After I uninstalled it and then reinstalled it as just regular user, the problem went away.

---

