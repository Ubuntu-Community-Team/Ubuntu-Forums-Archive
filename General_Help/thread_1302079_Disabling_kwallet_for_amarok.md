---
title: "Disabling kwallet for amarok"
date: 2009-10-26
forum: General Help
---

### Post by samuraitor on 2009-10-26
hey,

How do I go about disabling kwallet?Everytime I launch amarok, I get a Kwallet app asking for my password.Iwant to disable it.

---

### Post by lovinglinux on 2009-10-26
Go to "System Settings >>Advanced User Settings >> KDE Wallet" and untick "Enable the KDE Wallet Subsystem". This should prevent any software from asking for Kwallet passwords. Nevertheless, this might cripple some functionalities. For instance, I think you won't be able to save Konqueror passwords. I'm not sure tho, since I use Firefox, which doesn't have KWallet integration. What I know is that when I use Dolphin for remote network connections (ftp, ssh...) it stores the passwords using KWallet.

---

### Post by goldencako on 2009-11-02
I'm using gnome, so I don't have those menus. Do you know how I may do it from bash?

---

### Post by lovinglinux on 2009-11-02
> **goldencako said:**
> I'm using gnome, so I don't have those menus. Do you know how I may do it from bash?

Unfortunately no.

---

### Post by seeker5528 on 2009-11-02
In Gnome look for 'applications --> system tools --> system settings'

System Settings might not have got pulled in when you installed Amarok, hang on........

If I open Synaptic and select systemsettings and choose to remove it, then it doesn't list Amarok as one of the things to be removed, so looks like it probably doesn't get pulled in if Amarok is the only KDE thing you chose to install.

Later, Seeker

---

### Post by goldencako on 2009-11-03
So, I went ahead and installed systemsettings. Now it appears under System > Preferences, but when I open it, there's nothing about kwallet. Maybe I need yet another package? I wanna change the setting but not have to install the whole of KDE just to do that...

---

### Post by realzippy on 2009-11-03
Have a look at this thread please:

[http://ubuntuforums.org/showthread.php?p=8224848](http://ubuntuforums.org/showthread.php?p=8224848)

---

### Post by goldencako on 2009-11-03
Thanks a lot.

---

