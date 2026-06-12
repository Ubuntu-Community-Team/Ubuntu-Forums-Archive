---
title: "View networkin apps?"
date: 2011-10-03
forum: General Help
---

### Post by zero2xiii on 2011-10-03
Hay all,

I cant seem to find an answer in google for this? Maybe I am using wrong terms.

Is there a terminal command that can show me all the active connections outbound (and if possible inbound) from my ubuntu box? Even if it requiers an application install.

I have a system monitor widget on my top pannel, and some times is shows a LOT of internet traffic, even though I am not using ANY internet related software, I just want to be able to check exactly what is going on network wise.

No IP's neccesary (although it might be great..) but if possible, port and PROGRAM refference..

Thanks alot
Cherz

---

### Post by spiky001 on 2011-10-03
Dose this help ```
sudo netstat -aput
```

---

### Post by zero2xiii on 2011-10-03
Yep,

That does more or less. Is there other options? This one keeps running (Which might be a good thing I guess, for monitor purposes)

I have been on windows sooooo long ago I cant remember the command, but when I wanted the IP of a machine that was connected to me (FTP) I would enter the command and it showed all active connections with the IPs. Worked excelent. Was not live. But it did the job.

This command works, thanks :), just wondering if there is another more, passive, option.

Thanks for the speedy reply ):P

---

### Post by zero2xiii on 2011-10-03
Haha hold up,

This is perfect. Read trough the manual for "Netstat". It will do perfectly what I want to. Can even script this to do regular checks.

Thanks! :D

---

