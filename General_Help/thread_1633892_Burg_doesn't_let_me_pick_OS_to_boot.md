---
title: "Burg doesn't let me pick OS to boot"
date: 2010-11-29
forum: General Help
---

### Post by jasker on 2010-11-29
I am dualbooting Ubuntu 10.10 x64 and Windows 7 x64.

I am using Burg instead of Grub2 since I like the nice graphical display for choosing which OS to boot. Unfortunately, after I turn on the computer from "shutting down" after a Windows session, it automatically chooses Ubuntu and doesn't let me choose Windows. (If I just "restart" after a Windows session, I can choose which OS I want to boot just fine).

After Ubuntu loads, I can restart and *then* I get the option of which OS to choose, but this is extremely frustrating to have to load Ubuntu then reboot just to get Windows.

I am not using the OS Prober module (I disabled it, and have a manual entry in my 40_custom file for Windows).

Does anyone have any idea what might be the problem, or where I can start looking?  Are there any debug logs, etc I should post in this thread?

Thanks!

---

### Post by dcstar on 2010-11-30
> **jasker said:**
> I am dualbooting Ubuntu 10.10 x64 and Windows 7 x64.

I am using Burg instead of Grub2 since I like the nice graphical display for choosing which OS to boot. Unfortunately, after I turn on the computer from "shutting down" after a Windows session, it automatically chooses Ubuntu and doesn't let me choose Windows. (If I just "restart" after a Windows session, I can choose which OS I want to boot just fine).
...........
Does anyone have any idea what might be the problem, or where I can start looking?  Are there any debug logs, etc I should post in this thread?

Thanks!

Turn on USB keyboard support in your BIOS.

---

### Post by jasker on 2010-12-04
The only option in my BIOS is for "USB Legacy support" which is already enabled...

EDIT:  Disabling that option seemed to do the trick!   Thanks!

---

