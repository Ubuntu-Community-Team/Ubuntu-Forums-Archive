---
title: "How to see which software was uninstalled in Ubuntu Software Center?"
date: 2010-10-17
forum: General Help
---

### Post by abcuser on 2010-10-17
Hi,
today I have uninstalled some software from Ubuntu 10.10 from Ubuntu Software Center. Now I would like to see which software was uninstalled. So I clicked on History icon in the left panel and clicked on Removals tab. In this tab I see only "Monday" and this are old removals most probably done on Monday. But today is Sunday and I see no removals that was done today.

How can I see the software that I have removed from Ubuntu Software Center today?
P.S. Search box at the top-right is empty.
Thanks

---

### Post by sendblink23 on 2010-10-17
> **abcuser said:**
> Hi,
today I have uninstalled some software from Ubuntu 10.10 from Ubuntu Software Center. Now I would like to see which software was uninstalled. So I clicked on History icon in the left panel and clicked on Removals tab. In this tab I see only "Monday" and this are old removals most probably done on Monday. But today is Sunday and I see no removals that was done today.

How can I see the software that I have removed from Ubuntu Software Center today?
P.S. Search box at the top-right is empty.
Thanks

Have you tried rebooting the computer.. maybe it takes a cycle or time to show up in there... but to be honest I haven't used that feature... so I'm just making a random suggestion to try... it won't hurt to reboot ;)

---

### Post by john newbuntu on 2010-10-17
Actually just closing and re-opening the software center helps(at least in my case).  Looks like the view is not getting updated in real time.  Another option is to look at /var/log/dpkg.log and check the timestamps.  Search for words like "install" and "remove"

---

