---
title: "Keyboard layout changes on reboot ; can't delete previous keyboard layout"
date: 2011-09-23
forum: General Help
---

### Post by Governa on 2011-09-23
Newbie here with a keyboard preferences problem.

I'm using 11.04 on a Dell Latitude D620. I only recently started using Ubuntu full time and during installation I picked the UK keyboard layout as it matched my D620's keyboard.

I have today received my replacement keyboard (Portuguese from Portugal) and easily replaced the previous UK keyboard with this PT one. Imediatly after this I went to the Keyboard Preferences and under Layouts added Portuguese and removed United Kingdom. Keyboard was then working perfectly.

The problem: everytime I reboot, the keyboard layout is switched back to UK and I get this little keyboard icon on the top bar next to the clock saying "GBr". I have to manually switch to "Prt" everytime I reboot. I tried several times returning to Keyboard Preferences and removing United Kingdom again but keeps coming back after a reboot.

How can I prevent that? How can I make the Portuguese keyboard stick as the permanent choice and also remove that keyboard layout switcher icon on the top bar with the 2 keyboard choices?

Cheers

---

### Post by Governa on 2011-09-23
OK more problems to report. After posting my question I tried to solve the problem by going to Keyboard Preferences and again removing United Kingdom leaving only Portugal but then I clicked on "Apply System-Wide..."

When I rebooted I got stuck in the loading screen with the keyboard light continuously blinking.

I decided then to reboot in recovery mode and once again it got stuck during boot but this time I took note of this:

VBS: Cannot open root device UUID
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0.0)

I tried to reboot but this time selecting the option to load previous Linux version and it booted fine. If I try to reboot and let it load by itself it will again freeze at some point with the keyboard light blinking.

Please help! I'm completely lost now.

---

### Post by garolou on 2011-10-08
To resolve the keyboard selection issue refer to [http://ubuntuforums.org/showthread.php?t=1568439](http://ubuntuforums.org/showthread.php?t=1568439) post no 7.

---

