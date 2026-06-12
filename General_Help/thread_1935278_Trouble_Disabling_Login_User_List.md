---
title: "Trouble Disabling Login User List"
date: 2012-03-03
forum: General Help
---

### Post by kenn213 on 2012-03-03
Hey Guys,

I'm trying to disable the user list on the login screen in Ubuntu 10.04 but I'm having trouble. I opened gconf-editor and under apps/gdm/simple-greeter I checked disable_user_list and disable_restart_buttons. Next I tried rebooting, but to my surprise, the user list and restart buttons were still there. I then checked in gconf-editor again, but the boxes were still checked.

Is there maybe something I need to do to apply these settings? Any help is much appreciated.

-Kennedy

---

### Post by codemaniac on 2012-03-03
Please recheck if you changing the settings as sudo ..

Best Regards

---

### Post by kenn213 on 2012-03-04
> **codemaniac said:**
> Please recheck if you changing the settings as sudo ..

Hmm, good thought, however I tried launching with sudo gconf-editor and set the boxes that way. Then tried a reboot but still had the user list. Then I logged in as root just to check and sure enough, the boxes are still checked in gconf-editor.

---

