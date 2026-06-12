---
title: "Scanner for Win32"
date: 2010-04-23
forum: General Help
---

### Post by FinalShot on 2010-04-23
I have a usb, FAT32 formted, it was used and contains files from a win32 plaform, anyway is there a virus scanner on Ubuntu I can use to scan it?

---

### Post by mcduck on 2010-04-23
> **FinalShot said:**
> I have a usb, FAT32 formted, it was used and contains files from a win32 plaform, anyway is there a virus scanner on Ubuntu I can use to scan it?

Pretty much every Virus scanner you can find for Linux is intended for scanning for Windows viruses.

ClamAV is a popular choice (although primarily intended for mail servers and such), but Avast also has a Linux version of their desktop antivirus application..

---

### Post by FinalShot on 2010-04-23
Thanks, downloading avast now.

---

### Post by FinalShot on 2010-04-23
Is [this](http://www.clamav.net/lang/en/) the real ClamAV website?

---

### Post by Grenage on 2010-04-23
If in doubt, clamAV is in the official Ubuntu repositories.

---

### Post by FinalShot on 2010-04-23
What's the command for Termianl to get ClamAV?

---

### Post by hansdown on 2010-04-23
> **FinalShot said:**
> What's the command for Termianl to get ClamAV?

Hi FinalShot.

The terminal command is

```
sudo apt-get install clamav
```

---

