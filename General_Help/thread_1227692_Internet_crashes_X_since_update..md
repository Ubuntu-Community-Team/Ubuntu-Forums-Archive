---
title: "Internet crashes X since update."
date: 2009-07-30
forum: General Help
---

### Post by JasenGroves on 2009-07-30
Since yesterday's kernel update, any internet browser I use crashes X after a few minutes of using it. My cursor continues to move but nothing is clickable and my keyboard becomes non-functional. It only happens when I'm running Firefox or Chromium. The only solution I can find is shutting the power off and reboot.

The only thing I can think of is I'm running the PSB drivers from the Ubuntu Mobile launchpad for the Intel GMA 500 video card... But before the update yesterday, it ran fine.

Any ideas?

---

### Post by Johnny B on 2009-07-31
does ctrl+alt+F1 work?
what does dmesg say?
any other clues?

---

### Post by JasenGroves on 2009-07-31
> **Johnny B said:**
> does ctrl+alt+F1 work?
what does dmesg say?
any other clues?

ctrl+alt+f1 doesn't work... actually, once it crashes, the keyboard isn't functional. So ctrl+alt+* doesn't work, keeping me out of terminal and everything when it crashes. All periphrials are unrepsonsive after the crash except for the mouse, where the cursor moves but doesn't click.

---

### Post by JasenGroves on 2009-08-08
It turns out the issue wasn't the internet, but my hard disk. My computer started crashing while just sitting there. When I reinstalled recently, I formatted it as ext4 and that's when the problems started. So I went back, reinstalled as ext3, and the problem went away.

---

