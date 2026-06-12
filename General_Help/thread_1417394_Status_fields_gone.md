---
title: "Status fields gone"
date: 2010-02-27
forum: General Help
---

### Post by zaurus on 2010-02-27
Hello

I installed recently Xbuntu on my laptop. It worked well a couple of days then I lost all status fields on Xfce desktop. It should be easy to restore but I did not find how.
Please advice.

Other question:
I do not have a grube menu within boot to choose a kernel to run. How to fix this?

Thanks in advance.

---

### Post by POWMS on 2010-02-27
Open terminal and type xfce4-panel. This will restore them.
Now go to Applications/Settings/Session and Startup.
Go to the Application Autostart tab.
Click Add down the bottom.
Type Xfce4-panel in the command box.
Save and check the box with a tick next to the Xfce4-panel.
This will force the panels to load at every startup.
Xfce is notorious for looing the panels.

As for the grub, I'm not sure what you are asking here.......maybe someone else can help.

---

### Post by zaurus on 2010-02-27
Thanks POWMS for your help!
As for grub, I do not have a menu to choose what kernel to boot when I start my PC. It just load the default kernel as defined in grub.cfg. You know when you update a system you kan have severel kernels installed so you can choose which one to boot as well as rescue modes. That is what I am missing.

KR

---

