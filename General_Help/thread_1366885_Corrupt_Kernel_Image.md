---
title: "Corrupt Kernel Image"
date: 2009-12-28
forum: General Help
---

### Post by cajual on 2009-12-28
Reinstalled my Realtek Wifi drivers and uninstalled nVidia 195's to put back in the supported 185's, rebooted, and now my 2.6.31-17-generic image won't boot in either normal or recovery mode.  Gets stuck on a line without much meaning.  I should also mention that I reinstalled the linux-headers-2.6.31-17 prior to rebooting.  Any ideas?  Currently logged in under my 2.6.31-16-generic image.

---

### Post by falconindy on 2009-12-28
> **cajual said:**
> Reinstalled my Realtek Wifi drivers and uninstalled nVidia 195's to put back in the supported 185's, rebooted, and now my 2.6.31-17-generic image won't boot in either normal or recovery mode.  **Gets stuck on a line without much meaning.**  I should also mention that I reinstalled the linux-headers-2.6.31-17 prior to rebooting.  Any ideas?  Currently logged in under my 2.6.31-16-generic image.

To you, maybe. No idea what's going on if you don't post a log of the error and what preceeds it.

---

### Post by cajual on 2009-12-28
Will post some stuff as soon as possible.

---

### Post by cajual on 2009-12-30
> **falconindy said:**
> To you, maybe. No idea what's going on if you don't post a log of the error and what preceeds it.

Rofl, it turns out I was compiling a 32-bit package on a 64-bit kernel.  So much for paying attention.

---

