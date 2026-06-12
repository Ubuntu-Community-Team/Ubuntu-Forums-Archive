---
title: "Login Loopback"
date: 2012-04-06
forum: General Help
---

### Post by zamru713 on 2012-04-06
For reasons unknown, my main login screen fails to log me in. I click on my username, enter my password, and then the screen goes black for a second, and I am returned to the login screen. logging in as root allows me to avoid this problem. I am running Ubuntu 12.04 beta on an HP Pavilion dv3 with an Intel Core Duo processor. I'm pretty much a noob when it comes to this sort of thing, so please be patient and explain fully.

---

### Post by ajgreeny on 2012-04-06
> **zamru713 said:**
> For reasons unknown, my main login screen fails to log me in. I click on my username, enter my password, and then the screen goes black for a second, and I am returned to the login screen. logging in as root allows me to avoid this problem. I am running Ubuntu 12.04 beta on an HP Pavilion dv3 with an Intel Core Duo processor. I'm pretty much a noob when it comes to this sort of thing, so please be patient and explain fully.
If this is a default installation of Ubuntu you should not be able to login as root, as the root account is disabled.  I wonder if the fact that you have enabled the root account has caused this problem for you.

Why did you enable the root account in the first place?  It will make it very difficult for you to follow any recommendations for Ubuntu that you see on this forum.
See the RootSudo link in my signature for all the details and explanations.

---

### Post by zamru713 on 2012-04-06
I don't remember enabling root login explicitly, i guess I did it by accident somehow. Perhaps disabling root login would help?

---

### Post by zamru713 on 2012-04-06
I have done some googling, and found out that I should have an .Xauthority file in my home folder. After additional googling, I found out that instead of .Xauthority, there should be a folder for my user in /var/run/gdm/. There is not. Any idea on how I can fix this?

---

