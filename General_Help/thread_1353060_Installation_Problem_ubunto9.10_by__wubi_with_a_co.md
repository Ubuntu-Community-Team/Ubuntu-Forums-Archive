---
title: "Installation Problem ubunto9.10 by  wubi with a copy of Vista on laptop lenonvo g550"
date: 2009-12-12
forum: General Help
---

### Post by coderman11 on 2009-12-12
welcome all
i have problem with ubunto 9.10 on laptop lenovo g550 and found on my laptop windows vista.
first: i downloaded ubunto 9.10 and installed it by wubi not through cd and the installation is completed right and  i installed it from the windows vista like any programm installing .
i installed it in partiain C on my laptop and every thing was good,but
when i restart laptop to enter the ubunto appear from the boot two choise :
windows vista
ubunto 
i enter ubunto to show the desktop of the ubunto ,but dont appeare any thing it appeare balck screen nothing and dont happend any thing its take more time and not change any thing inthe screen its still black and dont appeare any thing .
i dont know why this problem appeare 
form my kind of laptop (lenovo g550) or from my vga card for laptop
pr what i dont know>
plz , i want solving my problem plz , ihope see ubunto lunix on my laptop

---

### Post by gordintoronto on 2009-12-12
This has worked for some people:
- press esc at the grub boot stage to get the boot options
- press e to edit the boot commands
- select the boot command that starts with "kernel" and press e again
- add the following text to the end of that command: i915.modeset=0 
- press enter and then press b to boot with the modified grub command

If that doesn't work, please have a look at this message thread:
[http://ubuntuforums.org/showthread.php?t=1309693&highlight=g550](http://ubuntuforums.org/showthread.php?t=1309693&highlight=g550)

---

