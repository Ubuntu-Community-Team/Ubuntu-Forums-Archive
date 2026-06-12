---
title: "Evolution in KDE"
date: 2011-02-23
forum: General Help
---

### Post by neanderslob on 2011-02-23
Howdy,

I'm using Evolution in KDE and everything's working well except for the notifications (calendar and new mail particularly).  I'm guessing those are in different packages?  Can anyone help me out on how to get these running?  Thanks! 

Oh and one more thing, regardless of my default browser, evolution opens things up in rekonq by default.  How might I get this working for firefox?

---

### Post by ankspo71 on 2011-02-24
> regardless of my default browser, evolution opens things up in rekonq by default. How might I get this working for firefox? 

Try going to System Settings > Default Applications > Web Browser:
Choose firefox instead of Rekonq.

If that doesn't work, you might have to configure alternatives for x-www-browser and possibly gnome-www-browser. You can either install 'galternatives' or use the following commands:

```
sudo update-alternatives --config x-www-browser
sudo update-alternatives --config gnome-www-browser
```


The answer to the first question might be to install mail-notification-evolution?

---

