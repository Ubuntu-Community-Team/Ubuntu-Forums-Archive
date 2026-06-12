---
title: "reboot chronjob not working"
date: 2011-06-27
forum: General Help
---

### Post by baz.g on 2011-06-27
Hi,

i have added "@daily shutdown -r now" to my root crontab (sudo crontab -e) but it does not seem to ever run. When i look at the chron log using webmin i can see that it tried to run and there was no error. also when i run it manually using webmin the system reboots fine, very wierd. i also tried using reboot -f in the crontab instead and that also worked when manually run but not on schedule.

the reason i know it didnt run is on webmin it shows the system uptime

this is the output of the chron log:
```

Jun 26 21:17:02 GrantLaptop CRON[3467]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 26 22:17:01 GrantLaptop CRON[3873]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 26 23:17:01 GrantLaptop CRON[4269]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 27 00:00:01 GrantLaptop CRON[4530]: (root) CMD (shutdown -r now)
Jun 27 00:17:01 GrantLaptop CRON[4630]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 27 01:17:01 GrantLaptop CRON[5005]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 27 02:17:01 GrantLaptop CRON[5416]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

---

### Post by Cheesehead on 2011-06-27
Cron will happily save output like error messages...if you tell it to.```
* * * * * root /path/to/command **2>&1 /tmp/cron-result-file**
```

Cron may not know where to find the 'shutdown' command, try including the full path. ```
* * * * * root **/path/to/**command 2>&1 /tmp/cron-result-file
```

---

### Post by baz.g on 2011-06-27
Ok, I will try that, thanks

 it doesn't explain why I can manually run the cronjob in webmin though?

---

### Post by Cheesehead on 2011-06-27
It works from webmin because it's a valid command and your syntax is correct.

Cron works in a different environment than a user at a terminal. Cron jobs do NOT inherit user environment variables like $PATH (which includes /sbin for sbin/shutdown) or $DISPLAY (for on-screen events and notifications). That's why full pathnames are good practice for crontabs.

And in case that's not the problem, enabling the error messages will tell you what is.

---

### Post by baz.g on 2011-06-28
ok, i have now setup with the filepath for shutdown (/sbin/shutdown) and it is set to run tonight - will report back here after midnight :)

---

### Post by baz.g on 2011-06-28
excellent! problem solved, thanks guys :)

---

