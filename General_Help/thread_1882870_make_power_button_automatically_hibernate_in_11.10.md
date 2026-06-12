---
title: "make power button automatically hibernate in 11.10"
date: 2011-11-18
forum: General Help
---

### Post by rajohns08 on 2011-11-18
how can i configure my power settings so that when i press the power button my laptop goes straight into hibernation?

---

### Post by rajohns08 on 2011-11-18
here is what i did:

1. open terminal
2. cd /etc/acpi/
3. sudo nano powerbtn.sh  
4. erased all the code and replaced with just the line "pm-hibernate"

---

