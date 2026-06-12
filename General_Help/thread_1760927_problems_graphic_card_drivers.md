---
title: "problems graphic card drivers"
date: 2011-05-17
forum: General Help
---

### Post by FabricioB on 2011-05-17
I'm having a problem whit my graphic card, ubuntu actulizazes the drivers but now, when I start the computer, it sais "out of range". Is my monitor way too old?:confused: my ubuntu version is 9.10. I'm using Windows, please, help!

---

### Post by seawolf167 on 2011-05-17
Check a couple things:

[LIST]
[*]is the vga/dvi cable plugged in to the correct ports on your monitor and computer?
[*]is your resolution in Ubuntu set too high for your monitor to handle (i.e. 1920x1080 when it can only accept 1280x1024)? You can start it in safe-graphics mode to check (hit escape at the grub menu, select safe mode)
[*]did you install the correct (if any) graphics drivers? can you use the graphics driver suite to adjust the resolution?
[*]can you do an "auto-config" on your monitor? (usually by entering the monitor's menu with the physical buttons on the monitor itself and finding something like "auto adjust")
[/LIST]

---

### Post by 3xp10r3r|X13 on 2011-05-17
It might be helpful if you tell us what graphic card you are using and what operating system.
I didn't get if you're trying to boot windows or ubuntu("I'm using windows" "ubuntu...")

Assuming you're trying to boot ubuntu, (so you're not able to boot?), just run it in the !safe mode!. If you were able to boot, using the safe mode, get rid of the drivers you've installed (I guess you meant by"using windows" that you are currently using windows to post the thread). So once you've deleted those drivers, try to solve the problem again.

Sry, just a bit confused by the description
Hope I guessed right and hope this helped :)

---

