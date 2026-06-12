---
title: "How Can I Recover My Installation?"
date: 2010-04-11
forum: General Help
---

### Post by SoulMazer on 2010-04-11
Well, I screwed up. Everything was fine until I installed the new version of Debian so that I could dual-boot between Ubuntu and Debian. Sadly, when I installed Debian, the grub listing it generated did not contain any Ubuntu listings. I tried following [this guide (link)]("http://ubuntuforums.org/showthread.php?t=224351") to no avail. Is there any way I can restore my old grub or at least be able to boot my Ubuntu so I can back everything up? (When I inserted a live-cd to try and backup my Ubuntu stuff, I found out I didn't have permissions to read at least half of it)

Please, I am quite desperate.

Thanks in advance.

EDIT: Okay, well I recovered my installation by manually installing a new grub on my old partition. Now, I have all my Ubuntu listings, but nothing else. Is there a command I can run to have grub re-generate its list of OS's?

---

### Post by 2hot6ft2 on 2010-04-12
Sure
```
sudo update-grub
```

---

