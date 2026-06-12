---
title: "Default set of startup applications"
date: 2010-01-22
forum: General Help
---

### Post by imblack on 2010-01-22
Hello,
While recently tweaking my system i deleted some startup applications from System->Preferences->Startup Applications. Now my themes and some other settings are not showing up while I login.

Can any one please post here the default set of startup application entries that come when you do a clean install? I am using Ubuntu 9.10 64bit

PS: If there is any work around to reset.

---

### Post by Brandon Williams on 2010-01-23
If you run 'rm -rf ~/.config/autostart', it should delete all customizations you've done to 'Startup Applications'. The next time you log in, it will run all the autostart applications specified in /etc/xdg/autostart/. As long as you haven't made any changes to the files installed in /etc/xdg/autostart/, then removing your own overrides should be enough for a full reset to the system defaults.

---

### Post by imblack on 2010-01-24
Thankyou very much, My issue is fixed now. Thanks again.

---

### Post by shell21 on 2010-05-17
nice info :)

---

### Post by mrashley on 2010-05-18
Thank you. This works for 10.04 too! :)

---

### Post by imblack on 2010-05-18
I guess Ubuntu people should add a reset button there just in case we mess it up again by experimenting :)

---

