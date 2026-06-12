---
title: "drums at login"
date: 2009-12-01
forum: General Help
---

### Post by dln9 on 2009-12-01
I have 9.10.  When the computer boots up, just prior to the login window appears, some annoying drum sound plays.  How do I turn that off?

---

### Post by jbrown96 on 2009-12-01
There's two places where that setting may be. In System-->Preferences or System-->Administration. Go to Sounds and there's options for what sounds the system makes. Just disable all of them. It may be something particular to the login manager. There should be something about gdm, login manager, session manager, etc. There should be an option to disable it.

---

### Post by john newbuntu on 2009-12-01
sytem->preferences->startup applications. Disable "Gnome Login Sound".

---

### Post by JoTrocken on 2009-12-01
This just disables the sound after logging in. The drums are still annoying as usual. Bad thing the sound-on-off-button of my notebook is not enabled before I log in.

---

### Post by junapp on 2009-12-01
does this help? the mv command in particular:

[http://ubuntuforums.org/showpost.php?p=8367187&postcount=12](http://ubuntuforums.org/showpost.php?p=8367187&postcount=12)

---

### Post by dln9 on 2009-12-01
Thanks to everyone for all the help.  

I had already edited the system sounds to be "No Sounds".  That didn't do it.  

I had already turned off the GNOME startup sound.  That didn't do it.  

I implemented junapp's suggestion.  That did it.

---

