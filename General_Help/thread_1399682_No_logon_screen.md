---
title: "No logon screen"
date: 2010-02-06
forum: General Help
---

### Post by Coltomis on 2010-02-06
I recently uploaded ubuntu onto my dead windows computer. During one of my sessions I turned off my computer and turned it back on. When I had turned it back on and booted up Ubuntu it showed the little white logo. the logo then after a couple seconds and nothing else happened. The screen was still lit up but it just stays black. 
I currently use version 9.10. If any of you could help me it would be greatly appreciated.

Thank you.

---

### Post by mushwars on 2010-02-06
I have seen this before if you hit escape it will show you a backtrace.

What I would do is when your computer gets past POST hit escape like crazy and you will get the grub menu, then choose the .14 kernel. That should boot just fine and you will be back in business. as far as a perminant solution, I dont have a clue, just edit you /boot/grub/grub.conf and move the .14 to the top so it will boot that automatically, you will not even notice a difference.

---

