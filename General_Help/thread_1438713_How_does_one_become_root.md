---
title: "How does one become root?"
date: 2010-03-25
forum: General Help
---

### Post by badaveil on 2010-03-25
I made a mistake with an application I installed so uninstalled that application, did a fresh installation hoping it would be a clean application but that mistake still persist. That application sits inside file system/usr/lib so thought if I were root I could manually delete that application folder, however I can't since I'm not root.

Any advise?

---

### Post by andrewthomas on 2010-03-25
use sudo```
 
gksudo nautilus

```
and navigate to the folder (if you are using ubuntu)

---

### Post by aysiu on 2010-03-25
Or if you're using the terminal: ```
sudo -i
```

---

### Post by yeleek on 2010-03-25
Google and find this page?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by badaveil on 2010-03-25
Good!Good!Good!. I will give it a try later. Thanks Guys:P

---

### Post by wrose51106 on 2010-03-25
I use sudo su to drop in.

-Bill

---

### Post by dcstar on 2010-03-26
> **badaveil said:**
> I made a mistake with an application I installed so uninstalled that application, did a fresh installation hoping it would be a clean application but that mistake still persist. That application sits inside file system/usr/lib so thought if I were root I could manually delete that application folder, however I can't since I'm not root.

Any advise?

Install the **nautilus-gksu** package and then you can open anything as root ("administrator") using nautilus.

---

### Post by badaveil on 2010-04-05
> **dcstar said:**
> Install the **nautilus-gksu** package and then you can open anything as root ("administrator") using nautilus.

I managed to install nautilus-gksu but it doesn't appear anywhere under the main menu. How come?

---

### Post by aysiu on 2010-04-05
> **badaveil said:**
> I managed to install nautilus-gksu but it doesn't appear anywhere under the main menu. How come?
Go to Places > Home

The right-click on a file.

---

