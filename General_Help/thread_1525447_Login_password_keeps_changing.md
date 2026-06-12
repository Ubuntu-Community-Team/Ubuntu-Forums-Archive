---
title: "Login password keeps changing"
date: 2010-07-06
forum: General Help
---

### Post by celtica on 2010-07-06
Hi,

Something weird is happening on my system - Last night I had rebooted my machine and when it came back up it would no longer accept my password.  My 7 year old son had been playing on the machine earlier so I assumed he inadvertently reset my password to something else. I rebooted again, added the rw init=/bin/bash was able to get in and reset my password. That worked, I was able to access with no problem. I was able to perform admin tasks, it would prompt for password and accept the password. I just went to edit a config file and all of a sudden it is no longer accepting my password again and (my son has been no where near it)?!!?

I am not even sure where to start troubleshooting this - I know I can reboot and reset the password again - but is there a way to figure out how this is happening.

Any help would be appreciated!

Thanks

---

### Post by robsoles on 2010-07-07
That is some sure weird stuff.

After logging on to the system using the password you reset to, please open a terminal and type

```
user@host:~$ **passwd**
```into the prompt and press [Enter], it will ask for your current password so enter the password you set by using the direct access method and then select a new password by typing it twice - set a different password than you used in the reset method.

If your password changes again after this I can only suggest that your system has been compromised - in this event (if your /home directory isn't in it's own partition or drive) you need to back up your /home directory and reinstall your OS.


*tip: Give your child their own login and don't give them SU/Admin authority on the OS you are letting them use.


I propose that 48 hours of using the system after changing password using terminal should reveal if it is OK or not.

---

### Post by celtica on 2010-07-07
Thanks for the reply!

I changed the password again, and will watch it for 48 hours.  Heh, yeah I made my son an account of his own with no admin privileges!

If I end up having to reinstall, my home directory is on a different partitiion so I think I should be good there.

Thanks Again!

---

### Post by robsoles on 2010-07-09
So, how's it going?

---

