---
title: "Strange Terminal Messages while booting - How do I log them?"
date: 2011-06-16
forum: General Help
---

### Post by revo8778 on 2011-06-16
AFTER the Plymouth boot splash, I normally are immediately taken to the login screen. However, now after the boot splash, I'm taken to a terminal view. It shows (in order) a login prompt, and then about 5 or 6 instances of an error related to disk access (I read disk id's and "host bus error." How do I log these errors so I can start researching them?

---

### Post by Tony Flury on 2011-06-16
> **revo8778 said:**
> AFTER the Plymouth boot splash, I normally are immediately taken to the login screen. However, now after the boot splash, I'm taken to a terminal view. It shows (in order) a login prompt, and then about 5 or 6 instances of an error related to disk access (I read disk id's and "host bus error." How do I log these errors so I can start researching them?

They are logged in /var/log/dmesg - I think that is the right path. The dmesg log files are saved on each boot - dmesg.0... etc .

---

### Post by revo8778 on 2011-06-16
Those log files don't contain the errors I observed at startup. Maybe somewhere else?

---

### Post by revo8778 on 2011-06-16
Nvm, errors caused by my leaving a CD in the drive.

---

