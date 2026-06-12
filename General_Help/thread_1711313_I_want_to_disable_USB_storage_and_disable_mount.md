---
title: "I want to disable USB storage and disable mount"
date: 2011-03-21
forum: General Help
---

### Post by pisit on 2011-03-21
my company plan to use ubuntu for desktop used, and i got some problem 1.they don't want user use usb storage 2.disable sudo and mount command 
now i had disable auto mount, plz help

---

### Post by tredegar on 2011-03-21
Blacklist the **usb_storage** module. That should prevent USB drives from auto-mounting.

Normal users (that is those who are not members of the **admin** group) are not permitted to use the **mount** command for devices that are not listed in **fstab**

Normal users are not able to use the **sudo** command

---

