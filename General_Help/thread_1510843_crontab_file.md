---
title: "crontab file"
date: 2010-06-16
forum: General Help
---

### Post by adeelm on 2010-06-16
Hi all,
             I want to schedule a few things on my Ubuntu 10.04 machine. I have edited the crontab file using crontab -e commad. Now what I want is that When that schedule run a mail should be sent to the root user. Is it possible and how...

Thanks 
Adeel.

---

### Post by dcstar on 2010-06-16
> **adeelm said:**
> Hi all,
             I want to schedule a few things on my Ubuntu 10.04 machine. I have edited the crontab file using crontab -e commad. Now what I want is that When that schedule run a mail should be sent to the root user. Is it possible and how...


Firstly you do not need to manually hack things in the crontab file, use the **gnome-schedule** package and you get a GUI interface.

Secondly you need the **mailx** package and a MTA installed to send mails (**postfix** is more than adequate) and script lines to send whatever e-mail message you want.

You can search out previous posts already in the forums for examples of what you want to achieve.

---

### Post by anglican on 2010-06-16
> **dcstar said:**
> Firstly you do not need to manually hack things in the crontab file, use the **gnome-schedule** package and you get a GUI interface.

Secondly you need the **mailx** package and a MTA installed to send mails (**postfix** is more than adequate) and script lines to send whatever e-mail message you want.

You can search out previous posts already in the forums for examples of what you want to achieve.
In your crontab you need a line like:
```
MAILTO=root@localhost
```Then whenever a job runs **and produces any output** (this is important, if there is no output there will be no mail sent) an e-mail will go to root.

H

---

