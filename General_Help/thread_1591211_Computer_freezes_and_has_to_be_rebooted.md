---
title: "Computer freezes and has to be rebooted"
date: 2010-10-08
forum: General Help
---

### Post by dmillerw on 2010-10-08
Lately, about once a day, my computer will completely freeze, and I have no other option then to restart it.

Problem is, whenever I restart my computer after this, it no longer recognizes my hard drives, sometimes fiddling with the connections helps, other times, simply leaving it alone, but everytime, it's the same.

It's really annoying, and I really cannot figure out the cause, I can only think of power supply, or dying hard drives, anyone got any other ideas?

---

### Post by mörgæs on 2010-10-09
Could be bad memory blocks. What happens if you run memtest from the GRUB menu? Might take all night.

---

### Post by robert shearer on 2010-10-09
For future reference, powering off/hard reset risks file corruption.

Here is a link to the right way to exit a freeze.

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

The commands put the keyboard into raw mode and allow file syncing and safe controlled reboot.
Worth writing down.

(sometimes you have to repeat the sequence to allow time for complete file syncing and it pays to go slow, 1 second pause between key sequences.)

If you want to shut-down rather than reboot then the last command should be Alt+SysRq+o   (o=off)
So.... rseiuo (raising skinny elephants is utterly outrageous ??)

---

### Post by dmillerw on 2010-10-09
> **robert shearer said:**
> For future reference, powering off/hard reset risks file corruption.

Here is a link to the right way to exit a freeze.

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

The commands put the keyboard into raw mode and allow file syncing and safe controlled reboot.
Worth writing down.

(sometimes you have to repeat the sequence to allow time for complete file syncing and it pays to go slow, 1 second pause between key sequences.)

If you want to shut-down rather than reboot then the last command should be Alt+SysRq+o   (o=off)
So.... rseiuo (raising skinny elephants is utterly outrageous ??)

Never knew of that, handy, although...I have no SysRq key...curse my minimal keyboard...

---

### Post by robert shearer on 2010-10-09
> **dmillerw said:**
> Never knew of that, handy, although...I have no SysRq key...curse my minimal keyboard...

SysRq key is usually doubled with PrintScrn.
If you have one that may work ??   Alt+PrintScrn+r  etc etc.

---

