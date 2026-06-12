---
title: "How do I troubleshoot Ubuntu?"
date: 2010-05-27
forum: General Help
---

### Post by Heathicus on 2010-05-27
I have a problem with my installation of Ubunutu that I would like to resolve, but I'd like to learn *how* to resolve such issues in the future.  I have two user accounts on my computer.  One for me and one for my son.  On my son's account, if he logs out, the screen goes black and the computer freezes (no Caps Lock or Num Lock lights blinking when I press those keys).  All I can do is power cycle.  This does not happen on my account.  His account can reboot just fine, just not log off.  It happens if I'm logged on and we "switch user" to him, and if it's just him logged on.

In Windows I know where to go to start troubleshooting this.  In Ubuntu, I'm lost.  Is there an Event Viewer type of thing somewhere?  Log files that would show me what is causing the system to freeze?

I'm running Ubuntu 10.04.

---

### Post by Ozymandias_117 on 2010-05-27
```
dmesg
``` you may want ```
dmesg | tail
``` if it's just happened to post the last few things or ```
dmesg | less
``` so you can scroll up and down through it.

All the log files you could possibly want are in ```
/var/log/
```

---

