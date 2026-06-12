---
title: "Suspend not working, and grub menu gone"
date: 2011-03-03
forum: General Help
---

### Post by layers on 2011-03-03
I have two problems, that I can live with, but they are just annoying for tha afact that I don't know how to fix them.

1. My suspend does not work. Hibernation works - after I turn on after the hibernation, screen is blank, I have to move the mouse for the login window to appear. For Suspend, I get to the black screen, but then nothing happens - when I move the mouse or Ctrl+Alt+Backspace, nothing. It is a laptop, if that makes a difference.

2. When booting, I get a table of choices - the new kernel, the old kernel, memtests and the long gone windows partition. There is no /etc/grub/menu.lst and I've got no idea how to change this. Can anyone help?

---

### Post by zSeries on 2011-03-03
I am a newbie but I have same problem with suspend and hibernatiion. I have just opened a separate post for that. For grub thing just do

sudo update-grub

Let it build the menu based on scanning your system. You can set parameters to manipulater how it builds the menu but you need to read the docs.

Hope that helps.

---

### Post by Quackers on 2011-03-03
If you are using 10-04 you won't have a menu.lst file, as grub2 is being used (not grub legacy) which doesn't have one.
Changes can be made by following this guide.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by layers on 2011-03-03
Alright, the booting menu is done the way I wanted. So, again I searched for the suspend issue, but no one seems to have the same problem as me (my hibernation works).

---

### Post by layers on 2011-03-04
Shameless Bump?

---

### Post by layers on 2011-03-05
Is it that no one knows how to do this, or is it that there is no such fix yet?

---

