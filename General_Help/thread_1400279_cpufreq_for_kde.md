---
title: "cpufreq for kde"
date: 2010-02-06
forum: General Help
---

### Post by linux4life88 on 2010-02-06
When I was running Gnome I would always download cpufreqd and set it to ondemand. On the top bar I would have an icon like the one shown below where I could easily change it from setting to setting. My question is once cpufreqd is installed how do get this icon to show up in KDE?

---

### Post by linux4life88 on 2010-02-09
I found an option in KDE menus to set CPU frequency to ondemand but still no easy access way to change this easily like cpufreq. Any help would be much appreciated.

---

### Post by patchwork on 2010-02-09
Well, if you're not worried about the graphical menus, you can create a small bash script that changes the governor. 
 I did just that, edited my sudoers file so I didn't need to enter a password whenever I wanted to scale back my cpus, and attached the script to a keyboard command.  Works great for me.

If you have interest in this approach, I'll post details.

---

### Post by linux4life88 on 2010-02-10
> **patchwork said:**
> Well, if you're not worried about the graphical menus, you can create a small bash script that changes the governor. 
 I did just that, edited my sudoers file so I didn't need to enter a password whenever I wanted to scale back my cpus, and attached the script to a keyboard command.  Works great for me.

If you have interest in this approach, I'll post details.

In my searching I did find people who had done that and examples. This is an option I'm considering. Thank you for the help.

---

### Post by patchwork on 2010-02-10
Sure thing.


EDIT:   did you need me to post my example or are you all set?

---

### Post by linux4life88 on 2010-02-13
> **patchwork said:**
> Sure thing.


EDIT:   did you need me to post my example or are you all set?

I'm all set, thank you.

---

