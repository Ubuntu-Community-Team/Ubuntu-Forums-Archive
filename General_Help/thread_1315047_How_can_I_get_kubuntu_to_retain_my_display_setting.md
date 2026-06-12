---
title: "How can I get kubuntu to retain my display settings and font sizes after rebooting?"
date: 2009-11-04
forum: General Help
---

### Post by abefroman99 on 2009-11-04
How can I get kubuntu to retain my display settings and font sizes after rebooting?

TIA

---

### Post by soapBAR2 on 2009-11-04
- Are you using the LiveCD, or do you have ubuntu installed to a hard disk? If it's from the LiveCD, it's very difficult (if not impossible) to save your settings, and is precisely the opposite of what the LiveCD was designed for. Install Ubuntu to hard disk if you want it to remember your settings.
- If you're booting from hard disk, are you running the systemsettings with appropriate permissions? AFAIK, systemsettings should prompt you if and when it needs to, but just in case, run 
```
kdesudo systemsettings
```
- Are you using the nvidia-settings manager? Remember that you need to run it as root, AND you need to click "Save Changes To X Configuration File" to commit the changes for next time. Just
```
kdesudo nvidia-settings
```

---

### Post by diederick76 on 2009-11-07
> **soapBAR2 said:**
> 
- Are you using the nvidia-settings manager? Remember that you need to run it as root, AND you need to click "Save Changes To X Configuration File" to commit the changes for next time. Just
```
kdesudo nvidia-settings
```

The nvidia tool allows me to configure things, but "Save Changes To X Configuration File" returns an xorg.conf parsing error. It turns out that the new Xorg doesn't need xorg.conf or something. I wonder why it does seem to work at your end.

---

