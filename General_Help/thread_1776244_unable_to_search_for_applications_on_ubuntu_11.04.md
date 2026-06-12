---
title: "unable to search for applications on ubuntu 11.04?"
date: 2011-06-05
forum: General Help
---

### Post by pythonscript on 2011-06-05
When I click on the application button on Ubuntu 11.04, no search results come up when I type in the search box. For example, if I type in "gedit" nothing appears, and no results appear for "text editor" either. I've tried all case variations, too. Gedit is just an example of a program I *know* I have installed but still won't come up in search. How do I fix this? Unity is quite useless without it. 

Thank you!

---

### Post by amauk on 2011-06-05
make sure you have unity-place-applications and unity-place-files installed

---

### Post by pythonscript on 2011-06-05
Thank you for the incredibly quick response; that worked perfectly. Out of curiosity, what does the code in your signature do? I've done virtually no coding in bash before so I can't quite figure out if it's real or pseudocode.

---

### Post by amauk on 2011-06-05
> **pythonscript said:**
> Out of curiosity, what does the code in your signature do?It's a satirical take on those who constantly complain about new Ubuntu releases, and proclaim that any new release is the worst ever and they're going back to the previous release

as for what is *actually* does...

- It stores the current 2-digit year & month (as used by the ubuntu release numbers)
- Sleeps for 6 months
- Gets the current 2-digit year & month
- Writes out that Ubuntu <current_year>.<current_month> is the worst release ever, and they're going back to Ubuntu <prev_year>.<prev_month>
- loops

> **pythonscript said:**
> I've done virtually no coding in bash before so I can't quite figure out if it's real or pseudocode.It's real code, not pseudo. But it loops indefinitely and each loop take 6 months, so there's not a lot of point in actually running it

---

