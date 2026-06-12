---
title: "how did i just fix this?"
date: 2010-10-16
forum: General Help
---

### Post by flyingsliverfin on 2010-10-16
my friend (who has a mac) was over and he showed me [this]("http://lifehacker.com/5665765/macbuntu-makes-your-linux-desktop-look-like-mac-os-x") since he knows i have ubuntu. however, im running 9.10 and the theme is meant for 10.04 or 10.10

so i installed it anyway (i forced it) and it didn't work well. everything was laggy, no top and bottom bar(mac stlye), etc so i uninstalled it using the provided uninstaller.
when it finished, everything seemed to be working fine in the tty1 i was using. Then, when i switched to graphical desktop, first thing i noticed was that all my customizations were gone. The top panel was back to normal. Second, compiz (my cube) wasn't working. Third, and worst, everything was lagging. I clicked on something and i had to wait around 5 seconds for it to actually do that.

i also noticed that compiz was eating up lots of resources, i killed it but that didn't help the lag. Feeling that it was still something with compiz, i started manually deleting compiz files in /usr. For some reason, things started working at normal speeds. I restarted and everything was working, except now i have the problem that im missing half the compiz files it needs to run are missing, and that the minimize, close, and restore buttons are on the top left (ive fixed that now using gconf-editor).

how did messing with the compiz files change anything as for the lag? and how did the macbuntu that was meant for 10.04 mess everything up?

---

### Post by cloyd on 2010-11-06
Like you, I installed Macbuntu. I used it for a couple weeks. Parts of it I liked. Now and then, it did something weird. Then today, I picked up the machine and the screen went black. Wouldn't boot again until I turned off and pulled out the battery. Rebooted, but . . . the touch pad wouldn't work. USB mouse would. Uninstalled Macbuntu, and had to reinstall compiz, and setup up all my effects and customization again. Still, touchpad did not work. Shut down, pulled out the battery, and then replaced it, turned it on, and it all worked again. Don't think I want to use Macbuntu again.

---

