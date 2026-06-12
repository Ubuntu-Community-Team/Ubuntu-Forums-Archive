---
title: "Migrating Thunderbird Account"
date: 2012-06-18
forum: General Help
---

### Post by eadwacer on 2012-06-18
I just had to reinstall Thunderbird (see: Thunderbird Keeps Crashing), and now I have the problem of migrating the old mail files (.thunderbird.old...) into the new install. What doesn't work is copying them from the old folder to the new one. At best, I get the folder names, but it claims the folder is empty (but Nautilus sees the .mbx and .sbd files). I also tried using ImportExportTools, but I get the same result -- empty folders. 

This is Thunderbird 12 on an Ubuntu 12.04.

---

### Post by ajgreeny on 2012-06-18
First delete the **Mail** subfolder from the new .thunderbird folder that has been made by the application before you try to copy the old **Mail** subfolder back, as otherwise the old and new will be merged which could cause your problem.

---

### Post by eadwacer on 2012-06-19
That worked, but it didn't solve my problem.

As an aside, under Mail, the real mail folder uses the name of the mail server e.g. mail.nw.centurytel.net. They had changed their server name since my old Mail folder was created, so I had to rename that subfolder to match the new name.

Once I did that, all my old mail was visible, and I thank you for some useful information.

The problem is, the original problem that killed TB, appears to be a corrupted .mbox in the old TB Mail folder. So when I brought it over, I brought over the old problem. 

So, let's call this one solved, and I'll roll everything back to the "Thunderbird crashes on startup" thread.

Thanks again.

---

