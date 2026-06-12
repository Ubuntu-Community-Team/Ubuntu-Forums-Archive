---
title: "Acer Aspire 5553G No battery recognized"
date: 2010-11-11
forum: General Help
---

### Post by kics82 on 2010-11-11
I am fairly new to linux hardly know how to use terminal so as idiot friendly would be great.

Problem:
Ubuntu works great had to fix my wireless but I got it working how ever I can't seem to get an indicator on how much battery life I have left. I checked into the sys>pref>pwr mng but all I see is On AC Power and General. 

Any help please :( again I am not very linux savvy so as idiot proof the better.

Thanks in advance

---

### Post by P4man on 2010-11-11
Open a terminal from applications > accessoiries > terminal.
Copy paste this command:

```
cat /proc/acpi/battery/BAT1/info 
```

(note: to paste in a terminal you can middle click, or press shift+control+v).

Copy paste the output back here. If no battery is detected, you could try the link in my signature and follow the instructions to boot once with "acpi_osi=" option and see if that helps.

---

