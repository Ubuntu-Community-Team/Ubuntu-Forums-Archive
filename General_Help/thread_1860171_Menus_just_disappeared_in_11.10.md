---
title: "Menus just disappeared in 11.10"
date: 2011-10-14
forum: General Help
---

### Post by JonasCoelho on 2011-10-14
Hi, yesterday I upgrade my 11.04 to the newer version on my HP Pavilion Dv4BR(dual-boot with windows 7 - Ubuntu) but now it's completely useless =(
I still am able to log in but after that my home screen has nothing at all but the top menu, which does not allow me to access any software, not even the ubuntu software center nor terminal and there isn't the log off/shutdown button too(I still am able to restart the pc by pressing the shutdown button on the hardware, making the shutdown menu appears).
I tried to take a snapshot of how it was and save it on Windows(I use to do it all the time), but now it doesn't work anymore because Windows says that the file is at "an unavaible location or has been removed" when I try to open it.

I tried to logging in into the recovery mode, but it was worthless. Trying to access by the previous versions doesn't work too.

Is there any way to fix it?

Thanks in advance and sorry about the english mistakes.

---

### Post by zemadz on 2011-10-14
While the default Ubuntu login is broken, try selecting Ubuntu 2D in the login screen. Top right icon near your account name.

---

### Post by JonasCoelho on 2011-10-14
I tried logging in on all the options available, none of them works...

---

### Post by fritz269 on 2011-10-14
I booted into the recovery menu in grub and ran to fix broken packages and it worked.

---

### Post by JonasCoelho on 2011-10-14
So, I tried to do this too after reading your post and he found some bugged files, however, an error happened while trying to get them(he said that he couldn't found *URL adress* and couldn't fix *package name*) and finished everything saying that any package had been removed, installed nor updated.

Just adding: I don't have any importante files on Ubuntu without a copy on Windows, so if there is any way to reinstall It as long as It **does NOT** affect any Windows file, I'm pretty okay with that.

---

### Post by JonasCoelho on 2011-10-15
Am I the only one with this problem?

---

### Post by wildmanne39 on 2011-10-15
Hi, install compiz-settings-manager then open it and make sure the unity plugin is checked, it has a habit of coming unchecked after first being installed, the same thing happened to me.

You can hit ctrl+alt+t then enter this command to open
```
software-center
```

Then once it is installed type this to open it.
```
ccsm
```
Thank you

---

### Post by JonasCoelho on 2011-10-15
Hi! Thank you very much for your advice, unfortunately the Unity plugin were already checked, so I unchecked it and then checked it again and a lot of windows just pumpped into my screen saying that Unity were conflicting with a lot of other plugins. I told him to just ignore them, however, it did not work, but at least now I know the reason why all that happened.
Before giving up, I tried to back to gnome typing
```
sudo apt-get install gnome-session-fallback
```then I restarted the computer and logged in using the gnome appearance and now evertything is working great =)

---

### Post by wildmanne39 on 2011-10-15
Hi, I understand, I do not know why ignore the conflicts is there, I alway choose to resolve the conflicts if asked and it works.
Thank you

---

