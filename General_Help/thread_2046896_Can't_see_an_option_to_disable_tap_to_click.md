---
title: "Can't see an option to disable tap to click"
date: 2012-08-23
forum: General Help
---

### Post by Mellifluous on 2012-08-23
I want to disable the highly annoying tap to click touchpad function which seems to be on by default but I can't see it in the preferences anywhere. Could someone please tell me how to disable it? Thanks.

---

### Post by marinara on 2012-08-24
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Disable_tap_to_click](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Disable_tap_to_click)

---

### Post by Mellifluous on 2012-08-24
> **marinara said:**
> [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Disable_tap_to_click](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Disable_tap_to_click)

Thanks. It says "@synclient MaxTapTime=0" is the command to do it but where am I supposed to type it in? In the console it says no command '@synclient' found.

---

### Post by kalehrl on 2012-08-24
> Edit ~/.config/lxsession/Lubuntu/autostart
You missed this part.
Add that at the bottom of autostart file.

---

