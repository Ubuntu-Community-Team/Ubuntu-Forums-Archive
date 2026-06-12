---
title: "how to not show mounted drive icons on desktop.?"
date: 2009-06-29
forum: General Help
---

### Post by agel1 on 2009-06-29
can somebody tell me how to not show mounted drive icons on desktop, thanks

---

### Post by Wiebelhaus on 2009-06-29
> **agel1 said:**
> can somebody tell me how to not show mounted drive icons on desktop, thanks

Just type in gconf-editor into the Alt+F2 run dialog to open the app. 

[IMG]http://www.howtogeek.com/wp-content/uploads/2007/05/WindowsLiveWriter/HideRemoveableDriveIconsfromYourUbuntuDe_F982/010520071178057478449516320.png[/IMG]

Browse to apps \ nautilus \ desktop:

[IMG]http://www.howtogeek.com/wp-content/uploads/2007/05/WindowsLiveWriter/HideRemoveableDriveIconsfromYourUbuntuDe_F982/010520071178057409601492898.png[/IMG]

Find "volumes_visible" and remove the check mark.

You should check out [Ubuntutweak]("http://ubuntu-tweak.com/") it does allot of these things easily but it does make for a lazy Linux user.

Cheers.

---

### Post by agel1 on 2009-06-29
> **Wiebelhaus said:**
> Just type in gconf-editor into the Alt+F2 run dialog to open the app. 

[IMG]http://www.howtogeek.com/wp-content/uploads/2007/05/WindowsLiveWriter/HideRemoveableDriveIconsfromYourUbuntuDe_F982/010520071178057478449516320.png[/IMG]

Browse to apps \ nautilus \ desktop:

[IMG]http://www.howtogeek.com/wp-content/uploads/2007/05/WindowsLiveWriter/HideRemoveableDriveIconsfromYourUbuntuDe_F982/010520071178057409601492898.png[/IMG]

Find "volumes_visible" and remove the check mark.

You should check out [Ubuntutweak]("http://ubuntu-tweak.com/") it does allot of these things easily but it does make for a lazy Linux user.

Cheers.thanks

---

