---
title: "Lucid Lynx won't boot. No recovery option on Grub2"
date: 2010-07-06
forum: General Help
---

### Post by smudge12b on 2010-07-06
After a lot of updates yesterday I have found that Lucid will no longer boot, I just get a blank screen that has a cursor flashing in the top left corner. I can't boot into recovery mode to see what the issue(s) might be because I took that option out when I ran update-grub.

My question is this, is there a way to run update-grub -either from a live-cd or grub-rescue mode- that would put the recovery boot option back in? I have already edited the /etc/default/grub file to comment out the field.

Thanks in advance.

---

### Post by Leppie on 2010-07-06
if you press the "e" key when at the grub menu while the option you want to boot is seleced, you will be able to modify the boot line. append the letter "s" at the end of the line and press CTRL+X to boot like that. it will take you to a menu from which you can choose the recory shell.

---

### Post by smudge12b on 2010-07-14
Thanks for that, it worked a treat.

---

### Post by Leppie on 2010-07-14
you're welcome, glad it helped :)

---

