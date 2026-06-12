---
title: "Install QtiPlot 0.9.8.6 in lucid"
date: 2011-05-26
forum: General Help
---

### Post by leandromartinez98 on 2011-05-26
Anyone had luck in trying to install a more recent version of QtiPlot in lucid (10.04)? I need an update of QtiPlot because the one available on lucid by default (0.9.8.2) is unable to open some origin files I have, and the newer version are (I've tested under a virtual machine with Natty installed).

---

### Post by 3xp10r3r|X13 on 2011-05-26
I don't see your problem. Aren't you able to upgrade your current version?

---

### Post by leandromartinez98 on 2011-05-26
Only if I upgrade the whole OS. And I don't want to do that until the next LTS version of Ubuntu.

---

### Post by 3xp10r3r|X13 on 2011-05-26
It's really weird, that you can't just upgrade your current version of qt, while it's not referring to a ppa source (it's there by default isn't it? - if not you would have to add the ppa to your repositories), without upgrading your whole system...

sry I couldn't help you

PS: You've got to enable "allow whatever section it's according to" using your software center or terminal - that might be it

---

### Post by leandromartinez98 on 2011-05-26
Actually the thing is that the newest QtiPlot needs requires a greater version of libc6 (>2.12). I don't have the courage for upgrading this library because of it, as it is a central system library. I would need an standalone executable of a newer version of QtiPlot, actually.

---

### Post by 3xp10r3r|X13 on 2011-05-26
fair enough, but I have to disappoint you...I didn't spot a download link for some tar.gz folder, you could extract to get your stand alone version, yet.

---

### Post by Pand5461 on 2011-05-29
leandromartinez98, i succeeded in compiling it from source. Can provide building instructions.
UPD: bump. This version does not have open source vers. of Origin, xls and ods import plugins.

---

### Post by leandromartinez98 on 2011-06-02
Just an update: I was unable to install the newest version of QtiPlot, but I was able to install the actual Origin 8.0 using Wine (my institution has a license for that).
So, my problem is solved. For the ones interested, the instalation of Origin 8.0 with Wine is straightforward once you add the file 

"mfc42.dll" 

to the 

~/.wine/drive_c/windows/system32 

directory. That file can be copied from some windows instalation, or downloaded from the internet.

---

