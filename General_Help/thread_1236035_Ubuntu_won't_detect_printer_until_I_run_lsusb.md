---
title: "Ubuntu won't detect printer until I run lsusb"
date: 2009-08-09
forum: General Help
---

### Post by wtelford on 2009-08-09
I have a headless ubuntu server running openvz. We frequently power cycle our printer and when we do the server can't seem to detect it again until lsusb is run. 

I've watched /var/log/messages when I power on the printer, nothing..
The first time I run lsusb the printer will not be present in the list, but when I tail /var/log/messages I see the machine picking it up. I run lsusb again, the printer is listed, and all network printing resumes.

Any ideas? Its no fun to have to ssh into my server every time I want to print.

---

### Post by Sef on 2009-08-09
What version of Ubuntu are you running?

---

### Post by wtelford on 2009-08-09
sorry bout that. ubuntu server 8.04

---

### Post by amac777 on 2009-08-09
A really bad solution (maybe do this at least until you figure out a real solution): set a cron job to run lsusb periodically.

---

### Post by wtelford on 2009-08-10
I had considered that, but usually I turn on the printer and expect to print right then. If I set a cron job to 5 minutes it'd still take a while for the printer to become available. Any more frequent that that and it seems a little excessive.

---

### Post by wtelford on 2009-08-10
bump.

---

