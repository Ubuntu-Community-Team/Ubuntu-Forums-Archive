---
title: "Error message: &quot;Non-system disk&quot;"
date: 2006-04-01
forum: General Help
---

### Post by ubuntuubuntu on 2006-04-01
My HD has 3 partitions (1 swap, 1 with Windows and 1 with Ubuntu). I always used the Acronis OS Selector to choose the operating system on the boot. For some reason, now, when I turn the computer on, I see the message "Non-system disk. Press any key...". When I press a key, Windows is initialized normaly (the OS selector doesn't appear). How can I fix this problem?
Thank you.

---

### Post by dcstar on 2006-04-02
[QUOTE=ubuntuubuntu]My HD has 3 partitions (1 swap, 1 with Windows and 1 with Ubuntu). I always used the Acronis OS Selector to choose the operating system on the boot. For some reason, now, when I turn the computer on, I see the message "Non-system disk. Press any key...". When I press a key, Windows is initialized normaly (the OS selector doesn't appear). How can I fix this problem?
Thank you.[/QUOTE]
It is most likely a problem with your setup (and nothing to do with Ubuntu), why not use Grub to do the OS selection?

---

### Post by ubuntuubuntu on 2006-04-02
[QUOTE=dcstar]It is most likely a problem with your setup (and nothing to do with Ubuntu), why not use Grub to do the OS selection?[/QUOTE]

Right now I have no access to my Linux partition. How can I install Grub?

---

### Post by fivedai on 2006-04-02
[QUOTE=ubuntuubuntu]Right now I have no access to my Linux partition. How can I install Grub?[/QUOTE]


reboot with ur  install cd
mount ur   hda1 hda* etc   corectlly 
then intall withount format ur disk 
after that 
it will warn ur that "can't intall "
then u can select intall grub
ok
warn: don not   continue install,just install grub only 
then reboot
so simply 
good luck

---

