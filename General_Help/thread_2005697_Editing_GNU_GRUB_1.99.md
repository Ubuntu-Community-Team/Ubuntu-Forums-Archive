---
title: "Editing GNU GRUB 1.99"
date: 2012-06-18
forum: General Help
---

### Post by waseembaraskar on 2012-06-18
Hi Every1 outthere,

How to edit GNU GRUB version 1.99. I want to edit boot entrymenu list so that 'The Default will be Windows XP instead of Ubuntu'.  
    In Dual boot environment where windows XP & ubuntu are OSs.
    
    when start my computer the screen shows as
    
    1 - Ubuntu
    2 - ubuntu -generic
    3 - memory test
    4 - windows xp

    I want to edit boot entrymenu list so that 'The Default will be Windows XP instead of Ubuntu'. ie windows xp should be on 1 position.

    Please help, any kind of suggestion or guidance is helpful.
    Thanks in advance.

---

### Post by kagashe on 2012-06-18
> **waseembaraskar said:**
> Hi Every1 outthere,

How to edit GNU GRUB version 1.99. I want to edit boot entrymenu list so that 'The Default will be Windows XP instead of Ubuntu'.  
    In Dual boot environment where windows XP & ubuntu are OSs.
    
    when start my computer the screen shows as
    
    1 - Ubuntu
    2 - ubuntu -generic
    3 - memory test
    4 - windows xp

    I want to edit boot entrymenu list so that 'The Default will be Windows XP instead of Ubuntu'. ie windows xp should be on 1 position.

    Please help, any kind of suggestion or guidance is helpful.
    Thanks in advance.
Count the line number in the Grub menu taking first line as 0.

$ gksudo gedit /etc/default/grub

Change 0 in this line to the desired number:
GRUB_DEFAULT=0

Save and close the file.

$ sudo update-grub

After running update-grub the default will change in grub.cfg

Kamalakar

---

### Post by plucky on 2012-06-18
Or if you prefer a GUI use [Grub Customizer](http://ubuntuforums.org/showthread.php?t=1664134&highlight=drs305+customizer)

Good Luck

---

### Post by waseembaraskar on 2012-07-22
Hey Hi,

Its working.
I got what I needed.

Thanks @kagashe :P

---

