---
title: "Update Manager Error Message"
date: 2010-02-24
forum: General Help
---

### Post by badaveil on 2010-02-24
Today Update Manager request me to update so I tried but got this message:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

...so I know now I cannot update.

How do I solve this problem?:confused:
Please advice. Thanks

---

### Post by PoHandle on 2010-02-24
This usually happens when there are multiple applications attempting to update your machine at the same time.  (eg: Synaptic Package Manager and Update-Manager are both open)  I have noticed from time to time that a package manager will be working in the background, and if I try to use Synaptic, I'll get a similar error.

To fix this, you can either wait for the other process to end or end it yourself.  Try rebooting your computer. That usually helps.

If you are still unable to get the exclusive lock, try opening a terminal and entering:
```
sudo rm /var/cache/apt/archives/lock
```

Hope this helps.

---

### Post by badaveil on 2010-02-25
Oh... is that what it was all about?

Thanks for giving me hope...and that valuable tip. If only Ubuntu could answer like you, that would be the day :D

---

### Post by PoHandle on 2010-02-25
Ubuntu is largely community-driven, and you will find that it's users will often provide better advice that any customer support service.  When looking for answers, I usually look for customer/user solutions rather than asking the company/provider first, and I usually get a better answer that way too.  This goes for most of my computer endeavors... not just Ubuntu.

---

### Post by badaveil on 2010-02-25
...you will find that it's users will often provide better advice that any customer support service.

Very, very true and probably more honest;)

---

