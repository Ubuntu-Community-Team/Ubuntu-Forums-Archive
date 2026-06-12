---
title: "sending email from localhost via the terminal?"
date: 2011-01-21
forum: General Help
---

### Post by sohlinux on 2011-01-21
Hello,

How can I send an email from localhost via the terminal? I don't need pop just smtp.

I believe this can be done with postfix which I have just installed but what is the command to input via the terminal, on my centos box I use the following to send the contents of some files which works just fine but what about sending through postfix on ubuntu?

```
sudo tail -50 /home/user/.bash_history | mail -s "bash history" email@mail.com
```

---

### Post by timgood on 2011-01-21
Install bsd-mailx (in repos) and then 'man mailx' will give you all you need to know. Quick too!

Hope this helps.

---

### Post by emarcelcom on 2011-01-21
SURE!

$ sudo apt-get install mailutils

$ tail -50 /home/user/.bash_history | mail -s "bash history" [email]user@email.com[/email]

---

### Post by sohlinux on 2011-01-21
> **emarcelcom said:**
> SURE!

$ sudo apt-get install mailutils

$ tail -50 /home/user/.bash_history | mail -s "bash history" [email]user@email.com[/email]


thanks but it doesn't send any email neither does it show any error. any ideas?

---

