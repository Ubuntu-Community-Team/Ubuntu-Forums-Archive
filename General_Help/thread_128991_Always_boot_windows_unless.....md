---
title: "Always boot windows unless...."
date: 2006-02-12
forum: General Help
---

### Post by shawn524 on 2006-02-12
Is there a way to automatically boot windows unless a key, like spacebar, is pressed? I love using ubuntu, but i only use it for certain things. Things i dont want to do on windows.

Can someone help me out? I couldn't find anything when i searched.

---

### Post by hw-tph on 2006-02-12
If you have the dual boot setup but it boots to Linux by default you can simply move the Windows entry (it should be a couple of lines long) in /boot/grub/menu.lst to just *above* the "BEGIN AUTOMAGIC KERNELS LIST" entry. Since the line "default 0" further up in menu.lst tells Grub to load the first entry, Windows will always be default if it is moved up above the automagic list.

You can also comment out the hiddenmenu entry. This will make the full kernel list visible.


Håkan

---

### Post by ajgreeny on 2006-02-12
You need to edit your /boot/grub/menu.lst as root and change the default from Ubuntu to Windows.  
First make a backup of the file, 
"sudo cp /boot/grub/menu.lst /boot/grub/menu.backup".
Look for the line 
default		0
and change the zero to the appropriate number entry for windows, remembering that numbering in linux starts at zero.  If you get it wrong and your computer won't start, just hit the restart button, or do whatever you need to to restart and at grub, manually select Ubuntu to boot up again and try a different number in menu.lst until you get it right.
Good luck.  Eventually you'll want to start ubuntu as default, I'll bet!

---

### Post by shawn524 on 2006-02-12
I can't seem to edit the file. It's marked as read only and wont let me run it as root. What am I doing wrong?

---

### Post by nanotube on 2006-02-12
that file should be edited as root. so, for example, to edit it with the "nano" editor, from the terminal type 
sudo nano /boot/grub/menu.lst
for more info about how to do stuff as root in ubuntu, read this page:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Cathbard on 2006-02-12
If you prefer you can also open a shell/terminal and type:
```
sudo gedit /boot/grub/menu.lst
```
if you don't like old style editors like nano. Personally, I use nano all the time but I'm an old bastard. lol

You may also want to change the timeout value as well. It's self explanatory.

---

