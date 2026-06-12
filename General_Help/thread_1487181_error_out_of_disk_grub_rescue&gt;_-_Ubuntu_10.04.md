---
title: "error: out of disk grub rescue&gt; - Ubuntu 10.04"
date: 2010-05-18
forum: General Help
---

### Post by scufkanc on 2010-05-18
In [this]("http://ubuntuforums.org/showthread.php?t=1454036") thread it's marked as SOLVED, but it isn't.

I installed Ubuntu 10.04 Side by side on my laptop, now I get this error directly on startup, nothing else:

[B]error: out of disk.
grub rescue>[/B]

I tried to "reinstall" grub from Live CD, no sucsess.
There is some solution by removing a line, i went to that file but found nothing similar to delete. No such code.

What should I do, use Windows booter? And how would I do that now that I can't acces windows.

---

### Post by Raygreen on 2010-05-18
If you have your Windows Disk you can boot to the disk. Get the C:\ prompt and then type fixmbr (enter) then type fixboot (enter). Reboot your computer and you should be back into Windows. That works for Windows XP. if you are using Windows Vista or 7, then you have to add BootRec.exe fixmbr and then BootRec.exe fixboot.

---

### Post by scufkanc on 2010-05-19
Thanks. Masterboot (windows-like) now offers me 2 choices, Ubuntu and WIndows XP.

When I choose Ubuntu, it doesn't start it, it starts: 

[B]GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported.... ]
sh:grub>
[/B]

So how do I boot Ubuntu now?

---

