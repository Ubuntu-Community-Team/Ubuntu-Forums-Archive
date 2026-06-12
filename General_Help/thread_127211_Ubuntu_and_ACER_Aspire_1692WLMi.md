---
title: "Ubuntu and ACER Aspire 1692WLMi"
date: 2006-02-08
forum: General Help
---

### Post by zemex34 on 2006-02-08
Well, I've a laptop Acer Aspire 1692WLMi and when I try to start the Ubuntu install cd, the computer stops on the message "Uncompressing Linux... Ok, booting the Kernel". What should I do? :confused: 

Please, HELP ME!!! I love Ubuntu!! \\:D/

---

### Post by BlacKoffee on 2006-02-08
I work at Circuit City, and I know that the Acers have some software compatability issues, but the 1692 has done okay so far. It may just be that this particular laptop can't support linux :S

---

### Post by kingsidy on 2006-02-08
disable acpi

---

### Post by zemex34 on 2006-02-08
How can I disable acpi?

---

### Post by lamego on 2006-02-08
Add acpi=no to your boot options...

---

### Post by ktogias on 2006-04-12
See also thread 37979
[http://www.ubuntuforums.org/showthread.php?t=37979](http://www.ubuntuforums.org/showthread.php?t=37979)

---

### Post by rabidphage on 2006-04-12
might not be acpi
try noapic 
the other common boot options are nolapic pnpbios=off acpi=off
try each one most probably it'll be noapic
read [this]("http://wiki.linuxquestions.org/wiki/APIC")

---

### Post by ktogias on 2006-04-12
See also [https://wiki.ubuntu.com/Ubuntu5.10OnAcerAspire1692WLMi](https://wiki.ubuntu.com/Ubuntu5.10OnAcerAspire1692WLMi)

---

