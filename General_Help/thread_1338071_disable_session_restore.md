---
title: "disable session restore"
date: 2009-11-26
forum: General Help
---

### Post by holiday on 2009-11-26
Since the latest update xubuntu has started restoring my previous session. I had this trouble before where XUbuntu ignores my preferences and my checkboxes at startup.I finally disabled it by deleting sessions and making the session directory readonly. I never want to restore my previous session so this is acceptable. 

However, after this latest update, my previous session is popping up again. I have to disable this because it is a feature that just drives me up the wall.

Anyone know where the sessions are stored now? 

Thanks.

---

### Post by Brandon Williams on 2009-11-26
I know that you've already checked some of these things, but here's the full recipe anyway.

First, open 'Settings -> Session and Startup'. Make sure that 'Automatically save session on logout' is not checked. Then, look in ~/.cache/session/ and delete any session files for xfce and xfwm. When you log out the next time, make sure that the 'Save session for future logins' box is not checked.

---

### Post by holiday on 2009-11-26
Thanks, yes. I've gone through the prescribed routine but it has no effect. I am furious. I so most definitely do not want to restore all the windows of my previous session. In fact, probably, I rebooted just to get rid of the zillion windows I'd in my wacky wildness started up!

This is not the first time I've been unpleasantly surprised by the poor QA on Ubuntu upgrades. I appreciate the effort everyone's putting into it, but - come on! My workstation at work is regularly updated by Microsoft and NOT ONCE has a MS update caused this level of havoc.

I know it's more fun to just code something fresh and new, but if you're going to be a serious distro?! You can't do this stuff. QA! Comprehensive QA!

Sure, I can get my grandmother happy with Ubuntu. I have done that. She didn't even notice. But I can not, so absolutely can NOT, tell her to accept upgrades until Ubuntu upgrades show some evidence of QA,

Rant off.

---

