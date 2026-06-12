---
title: "Crontab script for hibernate or sleep"
date: 2010-08-18
forum: General Help
---

### Post by JustGus on 2010-08-18
In order to shutdown my system at 11:15 every evening I've added the following script to my crontab file:

> # At 23.15 every evening shutdown with 1 minute's notice
15 23 * * * root shutdown -h +1

Rather than shut the whole system down, can anyone tell me how to set this up to simply put the machine in suspend or hibernate?  I've tried simply substituting these words for "shutdown" in the script, but it doesn't work.

Thanks for any suggestions.

---

### Post by mike2357 on 2010-08-18
I don't think there is a single, simple command like shutdown.  For some guidance, you can run "man pm-hibernate" and "man pm-suspend" and review the manual pages.  I didn't review them thoroughly, but it looks like there are some commands and options you can use.

---

### Post by JustGus on 2010-08-20
Thanks for the suggestion.  Had a look at the manual, but couldn't really see anything that looked like a solution (though that may be more because I'm not being particularly sophisticated in scripting!).  

What does the "pm" part of the line to bring up the manual refer to?  And would simply putting this into it work (don't want to simply try it, in case it does damage).  Would something like this work?

> 15 23 * * * root pm-suspend -h +1 

---

