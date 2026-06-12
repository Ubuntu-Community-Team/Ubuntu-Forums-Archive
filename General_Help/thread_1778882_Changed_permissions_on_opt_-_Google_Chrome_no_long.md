---
title: "Changed permissions on opt - Google Chrome no longer works!"
date: 2011-06-09
forum: General Help
---

### Post by cwrighta70 on 2011-06-09
Okay, I made a stupid move and changed the permissions on the /opt folder to 755 using:

sudo chmod -R 755 opt

Now, Google Chrome will not run.  When trying the google-chrome command, I get the following error:

[6806:6806:10932588232:FATAL:chrome/browser/zygote_host_linux.cc(123)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /opt/google/chrome/chrome-sandbox is mode 4755 and owned by root.
Aborted

Anybody know how I can fix?  What are the default permissions for /opt so that I can change that back?

Thanks,
Chris

---

### Post by ruffEdgz on 2011-06-09
Go into /opt/google/chrome then run the following command:
```

cd /opt/google/chrome
sudo chmod 4755 ./chrome-sandbox

```
Cheers!

---

### Post by cwrighta70 on 2011-06-09
Perfect!  Thanks a ton, ruffEdgz!

---

