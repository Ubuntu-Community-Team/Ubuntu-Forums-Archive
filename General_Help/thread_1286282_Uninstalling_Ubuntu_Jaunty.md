---
title: "Uninstalling Ubuntu Jaunty"
date: 2009-10-08
forum: General Help
---

### Post by GiantSpider on 2009-10-08
Hey I've given Ubuntu a good go but I'm disappointed in it. From my ATI 4890 card's drivers being worse than those from Windows to the Ubuntu partition being unbootable, Windows and LiveCD work fine. 

   How do I make grub pick Windows by default? Its bad enough that I lost my data in an encrypted folder in Ubuntu, but Ubuntu loads up by default unless I'm standing next to the computer when it starts up.

  I know one way is to wipe and re-install, but I installed Ubuntu on three computers and one is has an OEM version of Windows and I don't trust the recovery CDs.

---

### Post by jeremyswalker on 2009-10-08
I know there is a Windows way to do it, but it escapes me. However, you could boot from the LiveCD. Once booted, you need to edit the file boot/grub/menu.lst on your Ubuntu partition. Starting at 0, count the list of entries until Windows. Enter the number toward the top of the file where it probably says "default 0". You would replace the zero with the correct number.

---

### Post by GiantSpider on 2009-10-08
Alright I tried editing from livecd. I could edit the file but not save, I guess its read-only. The file was boot -> grub -> menu.lst. I couldn't edit on another computer either that was booted into Ubuntu, not live cd.

I tried typing gksu gedit /boot/grub/menu.lst but it just gave an empty menu. Not sure what I did there. Maybe I can overwrite the original menu, I guess I could copy the contents of the menu into the new menu edit and overwrite. I also tried navigating by terminal but I couldn't reach grub. 

I typed ls, saw .. typed cd .., then cd .., typed ls saw boot typed cd boot, typed ls and no grub typed cd grub didn't work. Tried ls -a still didn't see grub. Tried cd .grub and still a no go.

I got ```
sudo gedit /boot/grub/menu.lst
``` to work on the computer that I can reach the Ubuntu partition in, still working on the broken Ubuntu computer.

I think the problem is I'm in the live cd's filesystem rather than the 52.4 gb media's filesystem, which is my Ubuntu partition. How do I change directory to get inside my Ubuntu partition? I went cd Desktop and then ls, it has examples and ubiquity-gtkui.desktop listed but no disk drive. What the heck is ubiquity-gtkui.desktop anyways?

---

### Post by jeremyswalker on 2009-10-08
You are right to use gksu, but you do not want to edit /boot/grub/menu.lst while on the liveCD. You want to edit the file /path-to-ubuntu-partition/boot/grub/menu.lst. I'm not sure where exactly it would be mounted. Probably under the /media/<something> directory.

---

### Post by cariboo on 2009-10-09
If you want to change what os boots first, install startupmanager, it is in the repositories. You can use Add/Remove applications, Sysnaptic package Manage or the command line to install it.

---

### Post by GiantSpider on 2009-10-09
> If you want to change what os boots first, install startupmanager, it is in the repositories. You can use Add/Remove applications, Sysnaptic package Manage or the command line to install it.

I'm not sure if that works on live cd, I guess I could give it a go.

---

### Post by PrePenguin on 2009-10-09
If you can boot to windows you can run MSconfig and set windows as your default OS..Becareful of what you do though if you have never used the msconfig before.

---

### Post by GiantSpider on 2009-10-09
didn't work using live cd and installing startup manager trying searching for both start and manager couldn't find it in synapse or add/remove. I'll try msconfig tomorrow.

---

### Post by GiantSpider on 2009-10-09
Using msconfig didn't work. The default is set to Vista, I think its because I left grub in charge.

---

### Post by PrePenguin on 2009-10-09
If you can use the restore disk or if it has a restore partition you can fix the boot record that way.. Google Bootmgr.exe for windoes and you will see what I am meaning it will repair the boot record where just windows starts like normal. Vista is different then previous versions you cant use boot.ini you have to fix that boot record and there is a command for doing so i just cant remember it at this moment but its not hard to find.

---

