---
title: "im so lost"
date: 2010-07-02
forum: General Help
---

### Post by jamesg07 on 2010-07-02
ok so i wanted to try ubantu.. and i didnt like it because i know nothing about like programming so i uninstalled it and when i restarted my computer grub rescue> came up and any command ive tried is unknown... what do i do??

---

### Post by stlsaint on 2010-07-02
Exactly how did you install Ubuntu? Did you do a whube install or a dual boot install? If you did whube install than you just need to edit the windows boot.ini file to remove all grub entries. If you cant get to windows than you should be able to edit the file with the ubuntu livecd or whatever medium you used to install. If you did a live install than you need to hand the bootloader over to windows. If you have a windows install disk you can do that with it. Boot to the disk and re-install the windows bootloader.

---

### Post by jamesg07 on 2010-07-02
whats the difference in how i installed it??? because while it was on my computer it was like when i started up i got the option of what i wantd to use windows or ubuntu... but i dont have a windows disc

---

### Post by stlsaint on 2010-07-02
The way you installed it does matter and i described it in my first post of why it matters. So im going to go with the idea that you did a live install. And to be frank you dont need the entire windows disc. Just the recovery disc. So my suggestion would be to find a friend who has the same windows version as you and see if they have a disc or download a basic windows startup recover disc. Again it wont be the entire windows install disc so dont expect it but a simple startup recovery disc will install the windows bootloader back to your mbr!

---

