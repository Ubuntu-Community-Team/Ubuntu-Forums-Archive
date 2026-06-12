---
title: "Cannot Uninstall Gmail Notifier in Ubuntu 12.04"
date: 2012-05-24
forum: General Help
---

### Post by dbgrover on 2012-05-24
I installed Gmail Notifier but it hasn't functioned correctly since installation. When a new message arrives, the notification box pops up in the top right portion of my screen but when I mouse over the message, it fades and I am unable to click on it. 

I decided to just use the integrated messages application which is working fine. Now I want to uninstall gmail notifier but I can't. It's not showing up in the Software Center and when I tried to uninstall via terminal, I was not able to find it. Any advice? What would the proper path and application name be to uninstall in terminal? Maybe i'm getting something wrong there? 

Also, why would an application be operating on my system but not showing up in the software center?

---

### Post by kanikilu on 2012-05-24
How (and from where) did you install "gmail notifier"? Also, you said you tried to remove it from the terminal, what command did you use?

I see a PPA for something called "gm-notify". If that's where you got it from, try ```
sudo apt-get purge gm-notify
``` Or you can use "remove" if you want to keep config files...

---

