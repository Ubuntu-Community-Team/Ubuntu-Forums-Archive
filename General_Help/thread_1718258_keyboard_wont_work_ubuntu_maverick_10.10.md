---
title: "keyboard wont work ubuntu maverick 10.10"
date: 2011-03-31
forum: General Help
---

### Post by sparker1 on 2011-03-31
I just came back home after 8 days to find my keyboard doesn't work once I am in the system (i.e. after login). I haven't had a problem with my computer for so long I don't remember how to fix things now. Anyway, whenever I press a key I just get a weird error sound from the operating system but no input into Firefox, the terminal or any other proggy. It's a dual boot system and the keyboard works fine in XP. I did a repair broken packages but it made no difference. Grateful for any help......it's probably something simple but I have no idea where to start.

---

### Post by Mark Phelps on 2011-03-31
If it's a USB keyboard, look into your BIOS settings.  You should have some that deal with USB legacy settings.  Try toggling those (on, then off) to see if that makes a difference.

---

### Post by sparker1 on 2011-03-31
Thanks Mark but it is a PS2 type and I have tried two keyboards. I have found the problem and for anybody else that gets this, here it is - somehow, and I don't believe a human being did it, the item called "slow keys - only accept long presses" under preferences-keyboards, had become ticked. Untick it and you're good to go. Yes, there are ghosts in the machine!

---

