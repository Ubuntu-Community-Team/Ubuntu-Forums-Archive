---
title: "why my xubuntu randonly shows login screen?"
date: 2010-02-19
forum: General Help
---

### Post by ayet on 2010-02-19
Iam using the new xubuntu 9.10 and I set login automatically in the login screen in the systems menu. but on after every boot it shows the login screen many times even after a correct login, and sometimes it doesn't show. I already updated my system so what should I do so that no more login screens after boot?

---

### Post by ayet on 2010-02-20
any ideas?

---

### Post by bobcollard on 2010-02-20
> **ayet said:**
> any ideas?
Next time you have no login screen, go to Menu/Settings/Session and Startup then check "Automatically save session on logout"

---

### Post by ayet on 2010-02-20
still the same results, I tried session & startup automatically save session on logout. It still keep asking me to login every startup 2x or more sometimes.

---

### Post by bobcollard on 2010-02-20
> **ayet said:**
> still the same results, I tried session & startup automatically save session on logout. It still keep asking me to login every startup 2x or more sometimes.
Try System/Users and Groups and see if it is checked for Don't ask for password.  See screenshot, mine is not checked, I login.

---

### Post by ayet on 2010-02-28
still the same, just now I logged in 5 times on my systems all correct passwords.

---

### Post by ayet on 2010-03-02
any ideas what seems to be the problem here? Is it a defective harddrive?

---

### Post by bobcollard on 2010-03-02
> **ayet said:**
> any ideas what seems to be the problem here? Is it a defective harddrive?
I don't think it is the hardrive but something in startup.  Open Terminal and type in "sudo update-grub" (without the quotes)  Wait for it, sometimes it takes awhile.  When you get back to your normal cursor reboot.  
If that does not do the trick you might want to download and burn another copy of xubuntu then backup your home directory and start from scratch again.  Make sure to check  md5sum of the .iso before you burn and burn on a slow speed.

---

### Post by ayet on 2010-03-18
I switched back to ubuntu, My xubuntu grub is now damaged, I dont know what happened to it. Iam not going back to xubuntu it seems to have some bugs that I dont want to solve.

---

