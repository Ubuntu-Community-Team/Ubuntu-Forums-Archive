---
title: "auth.log and crontab help"
date: 2010-03-07
forum: General Help
---

### Post by Neezer on 2010-03-07
I have a script that runs cat /var/log/auth.log and sends the results in an email to myself. I do this for my server which has an open ssh port. I just want to keep an eye on things.

How often should I run the script in order to make sure that a bit of each overlaps. I put the script into /etc/cron.daily. Will that make it run once a day?

---

### Post by dcstar on 2010-03-07
> **Neezer said:**
> I have a script that runs cat /var/log/auth.log and sends the results in an email to myself. I do this for my server which has an open ssh port. I just want to keep an eye on things.

How often should I run the script in order to make sure that a bit of each overlaps. I put the script into /etc/cron.daily. Will that make it run once a day?

There are already utilities that do this: ```
man logcheck
```

---

### Post by flippo on 2010-03-07
for reference though, putting a executable shell script in cron.daily will execute it daily.

---

### Post by Neezer on 2010-03-08
Well, I got my first log sent to me. I have a few questions about it. There are a few entries that are bothering me.

one:
```

Mar  8 07:35:03 server sudo:     root : TTY=unknown ; PWD=/ ; USER=nathan ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Mar  8 07:35:03 server sudo:     root : TTY=unknown ; PWD=/ ; USER=nathan ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Mar  8 07:35:03 server sudo:     root : TTY=unknown ; PWD=/ ; USER=nathan ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port

```

At 730 I was at work this morning...I'm not sure what these mean.

Also I got this:

```

Mar  7 16:04:46 server sshd[2916]: Address 192.168.1.102 maps to lappy.local, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!


```

What could this mean? I know a few times I would log in with wired and then use wireless and logout....could that be what that is?

---

