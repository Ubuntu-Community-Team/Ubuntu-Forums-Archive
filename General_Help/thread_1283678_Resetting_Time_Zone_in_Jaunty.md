---
title: "Resetting Time Zone in Jaunty"
date: 2009-10-05
forum: General Help
---

### Post by Phoenix` on 2009-10-05
I may have just forgotten something from the last time I used Ubuntu, but I accidentally set the timezone wrong on the Setup screens. I have tried manually resetting the time by right clicking the time and clicking adjust time and date. Shortly after I do this the system will reset back to the original settings. Any Ideas?

---

### Post by wojox on 2009-10-05
Try it from System > Admin > Date and Time

---

### Post by tuxxy on 2009-10-05
To reconfigure your time zone open a terminal and enter this command;
```

sudo dpkg-reconfigure tzdata
```

---

### Post by Phoenix` on 2009-10-05
Wow... Apparently switching back to Windows for a month brainwashed me.... Thanks!

---

### Post by cnh on 2009-10-18
Is there any option to use when run dpkg-reconfigure tzdata without calling the screen, something like "dpkg-reconfigure tzdata America New York"?

---

