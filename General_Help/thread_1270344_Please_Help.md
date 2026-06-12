---
title: "Please Help"
date: 2009-09-19
forum: General Help
---

### Post by Tapas Bose, India on 2009-09-19
Hallo everybody.
I am facing a problem with my firefox for one month or over. I had enabled "Show text during boot" option from System -> Administration -> Start up Manager. From that text I saw some failure of loading of firefox 3.5. Like:

*Skipped: /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/private-files> not found at line 81 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-mail> not found at line 166 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-console-email> not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-gnome-terminal>  not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5
*Failure: /etc/apparmor.d/usr.bin.firefox-3.5 failed to load                      [fail]

I have uninstall and again install firefox-3.5 for 3 times. But the error message is still displayed during shut down and startup. 

Please Help Me..
Thanks in advance.

---

### Post by Bachstelze on 2009-09-19
These message just indicate that the AppArmor profile for Firefox failed to load due to some missing files. Is Firefox still working well?

---

### Post by Tapas Bose, India on 2009-09-19
> **Bachstelze said:**
> These message just indicate that the AppArmor profile for Firefox failed to load due to some missing files. Is Firefox still working well?
Yes. It is still working well.

---

### Post by Tapas Bose, India on 2009-09-19
Apparmor profile is not installed in my computer. Should I install it from synaptic?

---

### Post by Bachstelze on 2009-09-19
> **Tapas Bose, India said:**
> Apparmor profile is not installed in my computer. Should I install it from synaptic?

If you don't need it, there is no reason to install it.

---

### Post by Tapas Bose, India on 2009-09-19
I try to install apparmor profile from synaptic but n the terminal I saw 
Error: #include <abstractions/private-files> not found at line 81 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-mail> not found at line 166 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-console-email> not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-gnome-terminal>  not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5

---

### Post by NoaHall on 2009-09-19
If you don't know what it is, you don't need to worry about it.

---

### Post by Tapas Bose, India on 2009-09-19
> **NoaHall said:**
> If you don't know what it is, you don't need to worry about it.
Okay. Thank you.

---

