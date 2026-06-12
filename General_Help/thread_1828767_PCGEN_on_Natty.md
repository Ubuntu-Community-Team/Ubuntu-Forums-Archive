---
title: "PCGEN on Natty"
date: 2011-08-19
forum: General Help
---

### Post by Khelben Arunsun on 2011-08-19
I know this has been posted before by others, but I'm trying to get the character generator PCGEN with an alien-ed deb I created. 

I have installed Sun JRE, purged OpenJDK, set Sun Java as the default Java, (not in that order) and yet PCGEN still doesn't want to load any data sets. 

Could it be because I used alien to create the package from the rpm?

---

### Post by nylanfs on 2011-08-20
> **Khelben Arunsun said:**
> I know this has been posted before by others, but I'm trying to get the character generator PCGEN with an alien-ed deb I created. 

I have installed Sun JRE, purged OpenJDK, set Sun Java as the default Java, (not in that order) and yet PCGEN still doesn't want to load any data sets. 

Could it be because I used alien to create the package from the rpm?

Try and removing the options.ini and any settings files from the user setting dir. I've generally found that I have to do that for the first time load.

---

### Post by Khelben Arunsun on 2011-08-23
I figured it out. This here bozo was trying to run the thing from pcgen.jar by mistake :oops:

Don't do that! For some reason, I set my shortcut to use the .jar file instead of the .sh script. :lol:

---

