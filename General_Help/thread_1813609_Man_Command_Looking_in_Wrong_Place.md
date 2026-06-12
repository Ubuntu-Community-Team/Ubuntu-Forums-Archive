---
title: "Man Command Looking in Wrong Place"
date: 2011-07-28
forum: General Help
---

### Post by eclipsechasers2 on 2011-07-28
I needed a feature in w3m 0.5.3 at a time when the standard distribution included w3m 0.5.2. So, I downloaded the source, ran configure, make, and make install, and all was well - 0.5.3 in /usr/local/bin and /usr/share/local/man/man1, 0.5.2 in /usr/bin and /usr/share/man/man1. Now that 0.5.3 is part of the standard distribution, I did make uninstall, and almost everything is correct - just the standard Ubuntu version in /usr/bin and /usr/share/man/man1. Command works just fine. However, when I execute:
man w3m 2>temp
I see the following message in temp:
man: can't resolve /usr/local/share/man/man1/w3m.1: No such file or directory
I still see the correct man page. I just can't figure out why it still insists on trying the local version first. It's almost as if man has a cached version of the location of the man page. I haven't made any changes to /etc/manpath.config.
Any ideas how to clear this trivial, albeit puzzling, problem?

---

### Post by gmargo on 2011-07-28
> 
It's almost as if man has a cached version of the location of the man page.
That's because the "man" system as provided by the **man-db** package _does_ keep a cached version of the location.  

It will be updated once a day through its cron script **/etc/cron.daily/man-db**.  You can wait a day or just run that cron script manually.

---

### Post by eclipsechasers2 on 2011-07-28
Thanks. That answer sounds so right, and yet ...
sudo /etc/cron.daily/man-db
does not fix the problem (even after a reboot).
Likewise for:
sudo at now /etc/cron.daily/man-db

Nor does reinstalling man-db.

Is there some other command I should be trying other than those listed above.

---

### Post by eclipsechasers2 on 2011-07-28
Aha! The cron daily job for man-db didn't work, but the weekly job did! Thanks very much for pointing me in the right direction; don't know how I'd have solved this otherwise.

---

### Post by eclipsechasers2 on 2011-08-07
Just for completeness, it looks like the command:
sudo mandb
will do what is needed here.

---

### Post by gmargo on 2011-08-07
I think the reason that the cron.daily shell script did not seem to work was that it really started a background process (using **start-stop-daemon( 8 )** ) for the **mandb( 8 )** command.  So when the shell script exited, the man database update had not yet finished.  It was a timing thing.

---

