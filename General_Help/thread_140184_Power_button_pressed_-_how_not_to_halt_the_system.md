---
title: "Power button pressed - how not to halt the system?"
date: 2006-03-05
forum: General Help
---

### Post by barakori on 2006-03-05
My 1.5 year old son became fond of my PC's power button recently. I was using SSH from a laptop to my computer when I got the following message:

Power button pressed
The system is going down for system halt NOW!

I heard that it's possible to replace the command that executes when such a "soft" power button is pressed (I assume a long press on the power button would still turn off the computer forcefully). Where can I change this command? I would like to replace it with an echo or something similar that's not that harmful.

I need my computer up for most of the time, and my kid's too smart - I tried hiding the power button, but that's just more of a challenge for him. I assume changing the command would give me a couple of months until he learns how to 'sudo'...

Any help appreciated. Thanks.

---

### Post by MrDan on 2006-03-05
I changed it in the BIOS there was an option in it.

---

### Post by barakori on 2006-03-05
I couldn't find anything in the BIOS - it's a 6 years old computer...

---

### Post by amasidlover on 2006-03-06
Have a look in /etc/acpi, it contains all the scripts that run on ACPI events. The one you want is power.sh - you can then edit it or simply change it so it is no longer executable (chmod a-x /etc/acpi/power.sh).

Alex

---

### Post by barakori on 2006-03-06
Thanks Alex. Great answer. Just one quick note - it looks like the script is actually /etc/acpi/powerbtn.sh - I actually saw the following command in it:

/sbin/shutdown -h now "Power button pressed"

---

