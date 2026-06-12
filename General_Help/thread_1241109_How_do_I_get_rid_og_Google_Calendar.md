---
title: "How do I get rid og Google Calendar?"
date: 2009-08-15
forum: General Help
---

### Post by User_Name_Taken on 2009-08-15
Every time I log in, a window pops up asking me to login into google calendar.  I don't like this and I did not install this.  Can someone tell me how to remove this completely and entirely?

---

### Post by Hendronicus on 2009-08-15
Go to System>Administration>Synaptic Package Manaer and search for "Google" and select "Completely remove this program". That ought to do it.

---

### Post by User_Name_Taken on 2009-08-15
Ya, I tried that and it removed everything about Evolution except fot the icons.  There is no information anywhere in my file system about google.  It's just that login screen that pops up everytime I log in.  It's annoying.  
Maybe it's linked to something else?

---

### Post by Hendronicus on 2009-08-15
Thunderbird, maybe?

---

### Post by User_Name_Taken on 2009-08-18
No.  I uninstalled that...

---

### Post by HiImTye on 2009-08-18
when it pops up run

```
gnome-system-monitor
```

sort by 'CPU' making sure that the processes using the *most* CPU are at the top

 hit ok

the program will do some work and appear somewhere near the top

this should give you a clue about the program that is prompting you for a password

---

