---
title: "Power adapter bug in Ubuntu Notebook?"
date: 2010-06-30
forum: General Help
---

### Post by cje on 2010-06-30
I've installed ubuntu notebook 10.04 on an acer aspire one and experienced a strange problem;

every time I connect or unconnect the power adapter the laptop goes into hibernate (or suspend?) mode. I've tested almost every power option and hasn't been able to turn off this annoying behavior.

Is this is a known bug or is it I who doesn't get it?

Thanks for any suggestions.

---

### Post by cje on 2010-07-04
Okay. I've tested different settings. Now, i'm able to connect the power w/o putting the laptop into hibernate or suspend mode. Don't ask me how. Anyway, still the laptop hibernates/suspend when power is disconnected. 

Anyone having an idea why?

Thanks again for any suggestions.

---

### Post by hvbakel on 2010-07-04
Looks like you're suffering from this problem described in the sticky thread:

Ubuntu shuts down after unplugging Laptop power cord
A problem known with MSI wind and some Vostro users.

Current workaround is to open gconf-editor and browse to:
Code:

/apps/gnome-power-manager/general

And de-select the option use_time_for_policy

There is no need to restart, just close the configuration editor.

---

### Post by cje on 2010-07-04
Thanks for your reply and suggestion, hvbakel. 

Anyway, it didn't help. The power manager is still hibernate the notebook when unplugging the AC power....
I even tried a restart

---

