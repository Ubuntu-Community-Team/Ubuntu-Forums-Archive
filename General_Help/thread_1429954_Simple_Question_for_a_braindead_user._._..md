---
title: "Simple Question for a braindead user. . ."
date: 2010-03-14
forum: General Help
---

### Post by Richard Carlson on 2010-03-14
I'm running Ubuntu 9.10 64-bit and want to boot up into terminal so I can run and  install Nvidia Drivers (proprietary) as root. How do I do this? Is it Ctrl-Alt-F1 as the system boots up? I've seem to have forgotten?   Thanx   Rich

---

### Post by 2hot6ft2 on 2010-03-14
When you boot up choose recovery mode and then Shell Prompt when you get to the selections. The prompt will show up at the bottom.
Then if the driver is in your home folder use
```
cd /home/<yourusername>/
```
and ```
ls
```
to list the contents of the folder. And
```
sh NVI
```
hit the Tab button to autocomplete the command.
Enter
When done with the installer use
```
reboot
```
**********
If you're already in ubuntu then use Ctrl+Alt+F1
and use
```
sudo gdm stop
```
then if the driver is in your home folder use```
sh NVI
```
hit the Tab button to autocomplete the command.
Enter
When done with the installer use
```
sudo reboot
```

Hope that answers your question.

The recommended way to install graphics drivers is to use
System > Administration > Hardware Drivers

---

### Post by mikewhatever on 2010-03-14
You have to press the 'shift' key right after the bios screen. Grub menu is supposed to appear, where you can choose the recovery mode. Once booted, you should see a blue window with options, select root shell or similar. That's the terminal you are looking for.

---

### Post by 2hot6ft2 on 2010-03-14
Also if you use the Ctrl+Alt+F1 option you'll have to login and to get out of it use Ctrl+Alt+F7.

Personally I prefer the recovery mode option.

---

