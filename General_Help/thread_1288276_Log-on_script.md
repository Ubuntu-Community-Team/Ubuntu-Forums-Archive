---
title: "Log-on script"
date: 2009-10-11
forum: General Help
---

### Post by Bilg on 2009-10-11
What's the best way to execute a command after any user logs on? In my quest for knowledge I have discovered /etc/rc.local but was wondering if this is the best solution or if there is another way I should be making use of.

I want to delay mounting of encrypted devices until a user logs on rather than have it occur during boot, to allow SSH server to start first.

---

### Post by eric3_14159 on 2009-11-09
The two best ways I know are /etc/rc.local , if the program needs to be run as root and you're comfortable with scripts, or System -> Preferences -> Startup Applications (on Gnome, at least) if the program should be run as the user, and also if you prefer a GUI.

In your case, it sounds like /etc/rc.local is the best choice, in my opinion.

---

