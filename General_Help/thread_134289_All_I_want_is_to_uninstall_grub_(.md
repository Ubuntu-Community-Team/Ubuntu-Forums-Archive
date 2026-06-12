---
title: "All I want is to uninstall grub :("
date: 2006-02-21
forum: General Help
---

### Post by Leiki on 2006-02-21
This is so frustrating...it can't be this hard, can it?! I did amlost everything people have said at this thread: [http://ubuntuforums.org/showthread.php?t=24113&page=2&highlight=recovery+console](http://ubuntuforums.org/showthread.php?t=24113&page=2&highlight=recovery+console) and none of them have worked. And plus, when I try to do the "fdisk /mbr" thing, it always asks me for an administrator password and mine does not work at all (I'm the only person on this computer.)

Oh, what should I do?!

---

### Post by sylvester_0 on 2006-02-22
Ok, I can try to help you, but I'm confused. In the thread title it says you want to uninstall grub, but that link is on how to restore/repair grub. If you want to get rid of linux [-( and just go back to windows :-k (sorry cant imagine this) do "fixmbr" and "fixboot" from a windows xp recovery console. Needless to say those commands may be a little off, haven't used em in a while... 

ALSO, if you don't know your administrator password, try blank. However, I believe it differs in different versions of the XP install disk. I don't think the SP2 disc will let you use the recovery console with a blank password. In this case, you must use a linux password changer disk. Google it and don't use this for evil purposes.

---

### Post by alan.mckinnon on 2006-02-22
Leiki,

What is it that you are trying to achieve? You can't uninstall grub - it's the thing that kicks Ubuntu into when when you reboot. You can replace it with other programs that do the same thing, like lilo.

fdisk /mbr is a windows command. What it does is overwrite the grub program that ubuntu put there and replaces it with the windows equivalent - which can only boot windows. So you definitely don't want to run that, it will leave your machine in a condition where it can't boot Ubuntu. (You can still get it back but there's serious voodoo involved)

---

