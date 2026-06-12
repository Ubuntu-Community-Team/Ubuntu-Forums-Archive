---
title: "Can't Install Flash on Xubuntu"
date: 2010-03-28
forum: General Help
---

### Post by Spongejerk89 on 2010-03-28
Ugh, I need to get this computer back to my aunt ASAP, but I can't get flash on it. I'm using Xubuntu 9.10. I try to download APT Ubuntu 9.04, and it asks me what to open it with. The only option is apturl. When I choose that it says, "Unknown Channel 'karmic-partner'  The channel-partnet is not known"

Can someone please, please help me?

---

### Post by Brandon Williams on 2010-03-29
From the system menu, select 'software sources'. When the app opens, got to the 'other software' tab. Do you see an entry for the 'partner' repository there? If so, tick the check box and then click the close button. If you don't see an entry for the partner repo, click the add button and enter the following APT line:
```
deb http://archive.canonical.com/ubuntu karmic partner
```
After adding the source, verify that the checkbox is ticked and click the close button.

Once that's done, you should be able to run 'sudo apt-get install adobe-flashplugin'.

---

