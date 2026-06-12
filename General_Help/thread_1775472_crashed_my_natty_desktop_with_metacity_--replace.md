---
title: "crashed my natty desktop with metacity --replace"
date: 2011-06-04
forum: General Help
---

### Post by 68pontiac on 2011-06-04
I'm in need of a touch of help. I seemed to have crashed my X desktop and I never get a GRUB screen that allows me to boot into recovery. Long story short, I accidentally used metacity --replace (out of habit) when I lost my window decorations. This caused the panel and dash to crash and I couldn't get a terminal. So I forced a reboot and now I boot into a black screen every time. GRUB doesn't even give me my normal recovery mode option. After my BIOS posts it just shows me the purple splash screen then blackness. Any help here would be superb. I have a LiveCD standing by but don't know where to go from there.

---

### Post by wildmanne39 on 2011-06-04
> **68pontiac said:**
> I'm in need of a touch of help. I seemed to have crashed my X desktop and I never get a GRUB screen that allows me to boot into recovery. Long story short, I accidentally used metacity --replace (out of habit) when I lost my window decorations. This caused the panel and dash to crash and I couldn't get a terminal. So I forced a reboot and now I boot into a black screen every time. GRUB doesn't even give me my normal recovery mode option. After my BIOS posts it just shows me the purple splash screen then blackness. Any help here would be superb. I have a LiveCD standing by but don't know where to go from there.Hi, when you start the boot up process hit the left shift key and see if that gives the recovery window, if so try
```
sudo unity --reset
```

---

### Post by 68pontiac on 2011-06-05
Problem solved. Thank you. Also had to uninstall my fglrx drivers but that got me into safe mode. :-)

---

### Post by wildmanne39 on 2011-06-05
> **68pontiac said:**
> Problem solved. Thank you. Also had to uninstall my fglrx drivers but that got me into safe mode. :-)
Hi, your welcome, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

