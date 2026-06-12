---
title: "Google Chrome no longer works correctly after hibernating"
date: 2010-10-30
forum: General Help
---

### Post by jf1991999 on 2010-10-30
I have 10.10 installed with Google Chrome.  I used the hibernate function for the first time a week ago and now when I launch Google Chrome it takes about 90 seconds to launch and comes up with an unresponsive 'wait' 'kill' message.  It does eventually launch however it doesn't remember website logins between launches.

I tried to uninstall and reinstall Chrome but this didn't help. It still had old settings even after I supposedly removed Chrome completely.

I think that something has been screwed up with the Chrome settings when I did the hibernate.  Can anyone suggest how I might be able to restore the chrome settings?

---

### Post by aeronutt on 2010-10-30
When you removed Chrome, did you delete ~/.config/google-chrome ?

---

### Post by Quackers on 2010-10-30
Have you rebooted since?

---

### Post by jf1991999 on 2010-10-30
I used the synaptic package manager to delete chrome but nothing else.  I will try deleting the config file as suggested.

I have done multiple reboots and even tried to hibernate again but the behavior is the same.  I have noticed that the boot process has slowed down considerably since the first hibernation, even after I do a normal shutdown restart.

---

### Post by jf1991999 on 2010-10-30
Deleting the config folder has fixed the problem.  Thanks for the quick responses to my posts.

Google sync restored all my bookmarks and preferences, awesome product!!!!

---

