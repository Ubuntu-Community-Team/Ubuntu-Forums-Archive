---
title: "Help"
date: 2012-01-02
forum: General Help
---

### Post by Vexiant on 2012-01-02
Hello, I recently accidentally messed up my Ubuntu OS on one of my hard drives. Very long story. Anyhow, I have the old hard drive mounted and have extracted all 'unhidden' data. I need to download the .purple to get my pidgin logs; I'm fairly new to Ubuntu. I opened root terminal and tried cd'd my way to where the folder would be, but same as when I normally access it, it just shows the normal files. Does anyone know how I can get the files like this?

Edit: seems I can now go into the .purple file and I see where it says "AIM, IRC, MSN" and so on. So how to I move the folders to some other place?

Edit2: I found out how to move, so nothing really needed here much. However, a tutorial messed something up for my aim folder. Told my to type mv "aim" ~/desktop
I did and I can't find my aim folder on either desktop top now...

---

### Post by jefelex on 2012-01-02
Hi  - Are you sure it's not ~/user/Desktop?  check the root filesystem for /desktop

Only a thought, based on what you said!

John

---

### Post by chipbuster on 2012-01-02
> **jefelex said:**
> Hi  - Are you sure it's not ~/user/Desktop?  check the root filesystem for /desktop

Only a thought, based on what you said!

John

+1

Also check for a /desktop in your home folder.

---

### Post by oldos2er on 2012-01-02
> type mv "aim" ~/desktop

This would rename 'aim' to 'desktop', so check your home folder for 'desktop' (note your actual /home/user/Desktop folder is capitalized). The 'mv' command is often used as a way to rename files or folders, see ```
man mv
``` for more info.

To do a recursive copy, you'd want to run something like ```
cp -r /home/user/.purple/* /media/folder
``` for example.

To list hidden files (or dotfiles) and folders in terminal use ```
ls -a
```

---

### Post by Paqman on 2012-01-02
Did you move it as root? Root has it's own home folder located at /root.

---

### Post by Vexiant on 2012-01-02
Thanks so much, guys. It was in root/Desktop/ :P

---

