---
title: "places shortcut broken"
date: 2011-12-13
forum: General Help
---

### Post by new to linux help needed on 2011-12-13
ok so when i try to use my shortcuts at the top, in the places tab. i get the following error.

"Failed to execute child process "/media/A009-531F/GBA/VisualBoyAdvance.exe" (No such file or directory)"

i have tried using a file manager and going in and making them use that as the default program to run, and that didnt work.

whenever i go into the meedia folder i cant find teh A00-531F folder to delite it.

when i do try to use the forget association i get the following message.

"Could not find '/media/A009-531F/GBA/VisualBoyAdvance.exe'"

i have had problems with mounting stuff, could this have caused it?
what should i do

---

### Post by BC59 on 2011-12-13
Insert a USB pen drive and run:

```
mount /mnt/flash
```

---

### Post by BC59 on 2011-12-13
An easy way to unmount the unknown media is by installing from Ubuntu Software Center, the application Storage Device Manager. 

Then you open it and from the left pane you can see the sda partitions and this unknown media. You choose unmount from the right panel.

---

### Post by MartijnNL on 2011-12-14
Just another remark: Windows software (which I asume VisualBoyAdvance.exe is) won't run on Linux normally. Some of it can run under wine, but far from all.

---

