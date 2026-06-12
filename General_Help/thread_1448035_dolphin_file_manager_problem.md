---
title: "dolphin file manager problem"
date: 2010-04-06
forum: General Help
---

### Post by cariso9001 on 2010-04-06
I change my computer.
I use kubuntu,too.
When I use sudo to open dolphin.
Next time I got this message.
Configuration  file / home / administrator / .kde / share / config / kio_thumbnailrc can't write.
Please contact your system administrator.
I don't know how to solve this problem. :?:

---

### Post by lovinglinux on 2010-04-06
Probably because you have opened dolphin with **sudo** instead of **kdesudo**. When running graphical interfaces with administrative rights you must use **kdesudo**, otherwise the application can generate permission issues. I'm not sure about dolphin, but when you do what you did with Firefox, it uses the user Firefox profile instead of the root profile, so it changes the ownership of ~/.mozilla and screws up further Firefox operations, due to lack of permissions. 

Assuming **administrator** is your username, run the following code in a terminal to regain ownership of the kde config files:

```
sudo chown -R $USER:$USER ~/.kde
```

Don't replace any letters. Run the code above as is. The system will identify the user from the environmental variables.

---

### Post by cariso9001 on 2010-04-09
Thanks! :)

---

