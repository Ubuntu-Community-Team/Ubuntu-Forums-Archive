---
title: "Nvidia driver install killed display"
date: 2010-08-08
forum: General Help
---

### Post by doubtful wisdom on 2010-08-08
Can do nothing with the PC.  New install of 10.04 and was prompted to install Nvidia driver.  Did so.  Rebooted, now have nothing except a thin line at top of screen.  How can I remove this driver when I see nothing?

---

### Post by chopinhauer on 2010-08-08
> **doubtful wisdom said:**
> Can do nothing with the PC.  New install of 10.04 and was prompted to install Nvidia driver.  Did so.  Rebooted, now have nothing except a thin line at top of screen.  How can I remove this driver when I see nothing?

You can boot into rescue mode (press SHIFT during boot to access Grub's menu) and uninstall it from a console.
```
sudo apt-get --purge remove nvidia-current
```
should do it.

---

### Post by doubtful wisdom on 2010-08-08
I should have tried chopinhaurs' suggestion.  However, it was a fresh install, so I just started the install process again.  If the suggestion worked a lot of time would have been saved.  Thank you for your response.  I did not know about pressing sift to get to the menu.

---

