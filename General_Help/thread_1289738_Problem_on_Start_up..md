---
title: "Problem on Start up."
date: 2009-10-12
forum: General Help
---

### Post by Darkmage09 on 2009-10-12
Ok, just recently I am having a problem at start up. I've only had Ubuntu installed for merely 4 days. =P

When on start up, Firefox, skype, Pidgin, The Terminal, and thunderbird will start up with Ubuntu. I go to Start>System>Prefrences>Start Up, and I don't see neither of those in the list. I go to Options and the "Automatically remember running applications when logging out." is unticked. At this point I'm confused with this. I can do a hard shut down, or do a soft reset, and it does the same thing.

Ubuntu 9,04
HDD: 110GB
RAM: 4GB
Graphics: ATI Radeon X1200
Processor: AMD Athlon 64 X2 Dual-Core Processor 1.80 GHz.


Original OS was Vista, then the OS's also used on this machine was Windows XP and Windows 7. Now the only OS is Linux.

Thanks in advanced.

---

### Post by Darkmage09 on 2009-10-12
Bump? Any help would be appreciated. Thanks.

---

### Post by easoukenka on 2009-10-13
Try deleting files from ~/.cache/sessions

---

### Post by etnlIcarus on 2009-10-13
The, "session", will be remembered from the last time, "Automatically remember running applications when logging out.", was enabled.

- Enable it again.
- Close all open applications.
- Logout and back in again.
- Disable, "automatically remember running apps".

---

### Post by DeMus on 2009-10-13
What etn1Icarus wrote is in the System -> Preferences -> Startup Applications.

---

### Post by etnlIcarus on 2009-10-13
Since he mentioned toggling the auto session feature in the OP, that much is a given.

---

### Post by Darkmage09 on 2009-10-13
> **etnlIcarus said:**
> The, "session", will be remembered from the last time, "Automatically remember running applications when logging out.", was enabled.

- Enable it again.
- Close all open applications.
- Logout and back in again.
- Disable, "automatically remember running apps".


Thanks that worked. ;D Skype and pidgin starts up, but thats ok I guess. my main problem was FireFox and Terminal, somehow or another Thunderbird stopped yesterday. 

So far Ubuntu has been great to me. :) I've been using ubuntu off and on for a year now. and fully switched to it after my laptop crashed using Windows XP.

Thank you again. :)

---

### Post by etnlIcarus on 2009-10-13
If skype and pidgin are starting up automatically, you probably didn't exit them properly. Make sure their icons aren't still in the system tray (top-right corner, unless you've moved your panels around), then go through the enable>logout>login>disable process again.

---

