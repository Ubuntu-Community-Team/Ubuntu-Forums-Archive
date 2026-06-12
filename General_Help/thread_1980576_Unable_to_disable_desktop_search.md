---
title: "Unable to disable desktop search"
date: 2012-05-15
forum: General Help
---

### Post by peterthebike on 2012-05-15
I don't need to run Nepomuk or Strigi. But if I go to System Settings there is not a Desktop Search option to disable. Please help.

Running 12.04 under Ubuntu 2D.

---

### Post by bubbles90210 on 2012-09-16
In case anybody else has this problem, this is what worked for me in lubuntu 12.04:

"System Tools > Nepomuk File Indexing Controller" opened the Nepomuk controller in the system tray.  I right-clicked and selected "Configure File Indexing".  Under the "Basic Settings" tab, I unchecked "Enable Nepomuk Semantic Desktop" (I also unchecked "Enable Nepomuk File Indexer" first, but I think it was unnecessary because disabling Semantic Desktop disabled the file indexer).  Under the "Desktop Query" tab, I clicked "Customize index folders..." and unchecked the home directory.  I changed both settings at the same time, so I'm not sure which one actually fixed my CPU problem (or if both are necessary).

---

### Post by Epodx64 on 2012-09-16
> **peterthebike said:**
> I don't need to run Nepomuk or Strigi. But if I go to System Settings there is not a Desktop Search option to disable. Please help.

Running 12.04 under Ubuntu 2D.

I think Nepomuk and Strigi are both native to KDE and shouldn't be running under Unity

---

