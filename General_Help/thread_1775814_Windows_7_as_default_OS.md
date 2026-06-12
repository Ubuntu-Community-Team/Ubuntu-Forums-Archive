---
title: "Windows 7 as default OS"
date: 2011-06-05
forum: General Help
---

### Post by mrdolphin on 2011-06-05
I've posted her a few years ago and was helped extremely well. I installed windows 7 and unfortunately, it got rid of grub. I managed to fix it via upgrading from 10.4 to 11.04. However, my only problem now is setting up W7 as the default OS.

In startupmanager, I have W7 as the default OS, but when I reboot, grub still highlights/selects Ubuntu. I tried 

gksudo gedit /boot/grub/menu.lst

and set 0 to 4, but that doesn't work. So far that's what I've seen from what people said. Is there something different with 11.04 versus 10.04 on how to make W7 the default OS?


Thanks in advance!

---

### Post by pqwoerituytrueiwoq on 2011-06-05
[FONT=Courier New]gksudo gedit /boot/grub/menu.lst[/FONT]
is legacy grub
did you revert to it?

if not you want 
[FONT=Courier New]gksudo gedit /boot/grub/grub.cfg[/FONT]
then run [FONT=Courier New]sudo update-grub[/FONT]

---

### Post by drs305 on 2011-06-05
First, determine which Grub version you are using:
Grub legacy (0.97)
Grub 2 (1.96 or later)
```
grub-install -v
```

It's most likey Grub 2. If so, here are some links on setting the default:
[LIST]
[*]Grub Customizer: An excellent Grub 2 GUI app. Click on "Customizer" in my signature line.
[*]Tasks: How to set the default by editing the Grub 2 files. "Tasks" in my signature line.
[/LIST]

StartUp-Manager should be able to set the default, but it was designed and works best with Grub legacy. I'd recommend Grub Customizer for Grub 2 operations.

---

### Post by mrdolphin on 2011-06-05
I am trying out grub customizer. Under preference, it has "default entry." The different entry was automatically set to the 11th entry, which is Windows 7 (I don't know why there's so many, I limited the kernel versions to 2 previously).  I update grub via sudo update-grub and it still does not make windows 7 the default. Have an idea of what I am doing wrong?

---

### Post by drs305 on 2011-06-05
In Grub Customizer, did you select it via Preferences, General tab, default entry, then selecting the name or position from the dropdown box? Did you click the 'Save' button?

If the answer to all is Yes, then please download, extract and run the boot info script from the "BIS" link in my signature line. That will let us see the status of your boot files. 

After running the script a file called RESULTS.txt will be generated. Post the contents of that file here so we can review it.

---

