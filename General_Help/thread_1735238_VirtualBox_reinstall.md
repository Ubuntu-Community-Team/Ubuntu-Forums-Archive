---
title: "VirtualBox reinstall"
date: 2011-04-21
forum: General Help
---

### Post by noworldorder on 2011-04-21
I installed VirtualBox but it is a version that does not support USB.  So I understand that I need to uninstall and reinstall a different version.  Question:  when I uninstall virtualbox do I lose my virtual drive.  And if I don't lose the virtual drive, do I need to do anything when I iunstall the USB version of Virtualbox such that it knows where the virtual drive is.

thanks

---

### Post by user1397 on 2011-04-21
> **noworldorder said:**
> I installed VirtualBox but it is a version that does not support USB.  So I understand that I need to uninstall and reinstall a different version.  Question:  when I uninstall virtualbox do I lose my virtual drive.  And if I don't lose the virtual drive, do I need to do anything when I iunstall the USB version of Virtualbox such that it knows where the virtual drive is.

thanksthe virtualbox in the ubuntu repos is the open-source version which does not have certain features that the proprietary enterprise version has.  one of these features is support for a virtual usb controller.  i think the proprietary version is on the [website]("http://virtualbox.org") but i'm not entirely sure.

you wouldn't lose your virtual drives if you uninstall, they're in the /home/user/.virtualbox folder.  so if you reinstall you might need to re-add your entries and under storage > IDE controller you would point it to the /home/user/.virtualbox folder

---

### Post by mikewhatever on 2011-04-21
You may need to point the new VirtualBox to the virtual drive, if it's not in the default location (.VirtualBox/ or something like that).

---

### Post by noworldorder on 2011-04-21
Thanks for the replies

>  i think the proprietary version is on the [website]("http://virtualbox.org/") but i'm not entirely sure.

Does this cost $ since it is proprietary?

---

### Post by noworldorder on 2011-04-21
No I found out it doesn't cost anything.  I installed it and the extension thingy needed for usb to work

> To view the extension packs that are currently installed,           please start the VirtualBox Manager (see the next section). From the           "File" menu, please select "Preferences". In the window that shows           up, go to the "Extensions" category which shows you the extensions           which are currently installed and allows you to remove a package or           add a new one.

it works!

---

