---
title: "Always run program/script as root"
date: 2010-12-06
forum: General Help
---

### Post by RomanP on 2010-12-06
Hi everyone,

I have a script that I want to run as root without opening up terminal each time. The script is the launch script for VirtualBox in /usr/bin/VirtualBox and I need to run it as root each time I double click it or run it from applications menu.

Right now I am forced to open terminal and enter: sudo /usr/bin/VirtualBox


What can I do to make it always run as root? I can also modify the main VirtualBox executable which is in /usr/lib/virtualbox/VirtualBox if thats a better solution but in
the end i need /usr/lib/virtualbox/VirtualBox to run as root no matter where I launch it from.

Please help!

---

### Post by sisco311 on 2010-12-06
You don't need root privileges to run virtualbox.

Did you add your user to the vboxusers group?

---

### Post by RomanP on 2010-12-06
I don't know about the user group but I need to run it as root otherwise USB devices can't be connected.


If I don't run it as root (run as normal user) it works fine but all USB devices are disabled.

---

### Post by CharlesA on 2010-12-06
If your user isn't in the vboxusers group, you can't use usb devices inside VBox.

---

### Post by RomanP on 2010-12-06
How do I add him to this group?

---

### Post by sisco311 on 2010-12-06
> **RomanP said:**
> How do I add him to this group?

```
sudo gpasswd -a **username** vboxusers
```

replace **username** with the login name of the user.

After running the command you have to log out and log back in.

---

### Post by shoot2kill on 2010-12-06
Preferences/Admin --> Users & Groups --> Manage Groups
--> scroll to vboxusers --> Properties -->
click the box beside the member you want to add.

---

### Post by RomanP on 2010-12-06
Worked like a charm thanks so much. Hope this helps someone else in the future.

---

### Post by sisco311 on 2010-12-06
Cool!

Don't forget to mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

