---
title: "Samba domain login &quot;No logon servers&quot;"
date: 2010-01-20
forum: General Help
---

### Post by BraedonVickers on 2010-01-20
I have a custom pam setup for logging into a windows domain from Ubuntu 9.10 via samba. The setup is detailed in [this thread.]("http://ubuntuforums.org/showthread.php?t=1360319")

The setup is working fine on multiple computers(once samba and other relevant packages are upgraded to 10.04 versions to fix the issues described in the linked thread). However, i recently setup another machine to use domain login in this manner, and it refuses to allow login after startup before winbind is restarted. When you try to log in, it shows the message "No logon servers". After logging in as a local user, and restarting winbind, it doesn't seem to have any other issues.

I have tried the fix for this message [described in this howto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"), but it does not seem to work, possibly as the howto was apparently written for 8.04.

Anyone have any ideas other than setting a script to restart winbind at some point in boot?

thanks,
   Braedon

---

### Post by BraedonVickers on 2010-01-23
Bump!

---

### Post by BraedonVickers on 2010-01-25
ReBump (any ideas, anyone?)

---

