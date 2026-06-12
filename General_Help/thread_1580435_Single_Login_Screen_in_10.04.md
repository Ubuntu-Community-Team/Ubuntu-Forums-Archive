---
title: "Single Login Screen in 10.04"
date: 2010-09-23
forum: General Help
---

### Post by zelkova on 2010-09-23
Hey all. I was wondering if anyone could tell me the least complicated method that would allow me to change the login screen so that, all of the accounts on the computer are not displayed at startup.

For example: 

Instead of ubuntu starting up, and going to the default login screen where it would list accounts like "Suzy's account, billy's account, johnny's account, and so on. It would be better if we could open up to a login screen where each user must type in their credentials, without seeing what other accounts exist on the machine. 

Information is appreciated.

---

### Post by sisco311 on 2010-09-23
To disable the user list, open a terminal (Applications -> Accessories -> Terminal) and run:
```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list "true"
```

To (re-)enable the user list, run:
```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list "false"
```

---

### Post by zelkova on 2010-09-23
Thanks for the help!

---

### Post by sisco311 on 2010-09-23
> **zelkova said:**
> Thanks for the help!

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

