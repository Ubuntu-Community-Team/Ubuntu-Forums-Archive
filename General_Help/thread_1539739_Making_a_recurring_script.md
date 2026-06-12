---
title: "Making a recurring script"
date: 2010-07-26
forum: General Help
---

### Post by Shamess707 on 2010-07-26
I have a script that I want to run at a regular interval, say every two hours. How would I go about doing that. Thanks in advance!

---

### Post by Zeike on 2010-07-26
Hi! Take a look at this Cron howto: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Shamess707 on 2010-07-26
Exactly what I was looking for. Thank you very much!

---

### Post by banskt on 2010-07-26
U might use crontab.

[ How to edit crontab ]("https://help.ubuntu.com/community/CronHowto")

1. Save your script as an executable file (something like filename.sh)

2. Make it executable (chmod +x filename.sh)

3. Include it in crontab (see above documentation)

Edit: Never mind... I was a bit late.

---

