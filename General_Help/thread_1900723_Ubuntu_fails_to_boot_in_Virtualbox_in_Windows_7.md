---
title: "Ubuntu fails to boot in Virtualbox in Windows 7"
date: 2011-12-27
forum: General Help
---

### Post by tranduyhung on 2011-12-27
Hi,

I installed a minimal Ubuntu 11.10 (only command line, no GUI) in Virtualbox 4.1.8r75467 in a Windows 7 machine.

When booting, after the GRUB screen appears and I select Ubuntu, Ubuntu only show a dark screen with a flashing cursor and then do nothing. Pressing Ctrl-Alt-Del makes Ubuntu restart as usual.

I have no idea how to figure out what's wrong to fix.

Do you have any suggestion for me?

Thank you very much!

---

### Post by xyzzyman on 2011-12-27
Can you switch to other vt's (ctrl-alt-f2, ctrl-alt-f3...) if not are you able to select 'recovery' at the grub menu and get to the recovery screen?

---

### Post by tranduyhung on 2011-12-27
Thank you very much, xyzzyman!

Pressing Ctrl-Alt-F1 shows me the login prompt. How could I not think about this Ctrl-Alt-F1 key combination at the beginning! :)  I thought that Ubuntu should have showed the login screen automatically.

---

### Post by xyzzyman on 2011-12-28
> **tranduyhung said:**
> Thank you very much, xyzzyman!

Pressing Ctrl-Alt-F1 shows me the login prompt. How could I not think about this Ctrl-Alt-F1 key combination at the beginning! :)  I thought that Ubuntu should have showed the login screen automatically.

It's because it's still going to VT7 even though you aren't loading a GUI.

---

