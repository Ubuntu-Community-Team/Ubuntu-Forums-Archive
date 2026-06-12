---
title: "unstable 12.04"
date: 2012-07-21
forum: General Help
---

### Post by fabio61 on 2012-07-21
After I installed the new 12.04 everithing went well up to a few days ago when the system started crashing more and more often, I receive error messages about updating of packages (it was impossible to update google chromium) and the system freezes quite often.

I am pretty sure that there must be som log file that can help me in understanding what is going on but I am not sure where to start. Can anyone help me?

---

### Post by Marcelo Ruiz on 2012-07-21
If the system crashes and shows you the report dialog, you can click on the "more info" button to know who the culprit is, and then you can google about it. For example if the program giving you trouble is compiz, you can google "Ubuntu 12.04 compiz problems".
To take a look at the log files, you can use the Log File Viewer. I would take a look to kernel.log, dpkg.log, syslog, Xorg.0.log. If some of them are not listed in the left column, you can open the file within that program. Remember log files are located in /var/log (there are more than the ones I just mentioned there, so if the program that gives you trouble has a log file, you can open it and find out what's wrong).
I hope this helps you.

---

