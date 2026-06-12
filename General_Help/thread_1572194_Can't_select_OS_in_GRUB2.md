---
title: "Can't select OS in GRUB2"
date: 2010-09-10
forum: General Help
---

### Post by nLinked on 2010-09-10
Using Ubuntu 10.10 Beta (don't think this matters specifically).

For some reason I can't select any OS in my GRUB menu. It was working before and now it doesn't. Normally I can use the down arrow on my keyboard to select an entry.

If I do that now, the countdown immediately ends and boots into the first entry. Same with any key really. Whatever key I press in the menu, it acts as though I pressed enter and goes straight into the first OS.

I want my selections working again. What's gone wrong?

I have reinstalled GRUB from a Live CD, my entries are all there, but pressing any key or arrow just ends the 10s countdown and boots the first entry. I'm so confused!

**SOLVED:** This was an issue with my Logitech keyboard and mouse. I have these 2 devices paired into one Logitech wireless receiver using their Unifying software. For whatever reason it became corrupt. Solved by booting into Windows which is on my other HDD, and removing the USB wireless receiver and plugging it in again. Then booting back into Linux HDD and I can use the keyboard again in GRUB.

---

