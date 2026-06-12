---
title: "Ubuntu Shuts Down Laptop on Suspend"
date: 2012-03-03
forum: General Help
---

### Post by andycastille on 2012-03-03
After updating to 11.10, clicking on the Suspend option shuts down the laptop completely. I upgraded to 12.04 beta, and this is still an issue. This wasn't a problem in 10.04, which I used for a while.

---

### Post by HavarN on 2012-03-03
Have a look at this page. You will find the power & suspend buttons configuration in dconf-editor @ org/gnome/settings-daemon/plugins/power

[http://askubuntu.com/questions/66723/how-do-i-modify-the-power-options-in-ubuntu-11-10](http://askubuntu.com/questions/66723/how-do-i-modify-the-power-options-in-ubuntu-11-10)

---

### Post by andycastille on 2012-03-03
UPDATE: Pressing a key will boot it back up, but I get a screen saying "VAIO" (as if booting from shutdown state), then some text flashes on and off the screen (as normal), the screen turns purple and the ubuntu loading animation appears (all as normal), I get a login screen, but when I log in, everything is closed, as if booting from nothing. 

That link is to disable the prompt. I have another problem. I might have found a fix here, as this seems to be a common issue: [http://askubuntu.com/questions/67130/sony-vaio-fw350-reboots-instead-of-waking-up-after-sleep-suspend](http://askubuntu.com/questions/67130/sony-vaio-fw350-reboots-instead-of-waking-up-after-sleep-suspend)

---

