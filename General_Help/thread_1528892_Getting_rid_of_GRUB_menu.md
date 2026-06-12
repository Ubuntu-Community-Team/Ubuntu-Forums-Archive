---
title: "Getting rid of GRUB menu"
date: 2010-07-11
forum: General Help
---

### Post by Acheron3 on 2010-07-11
Hi,
I've just moved from Windows-Ubuntu dual boot to Ubuntu 10.04 single boot. However GRUB menu stills appears when I power my on my computer. I would like to boot directly on Ubuntu (the only OS installed) when I power on the PC. I've googled it but I've not found the answer to the problem so I would be very pleased to receive your help. 
Thanks in advance!

---

### Post by Naitsirhc Hsem on 2010-07-11
run in the terminal 
```
sudo gedit /boot/grub/grub.cfg
```
find ```
set timeout=10
``` and change it to ```
set timeout=0
```

---

### Post by Acheron3 on 2010-07-11
Thank you! it works!

---

### Post by libssd on 2010-07-11
In grub2, much better to edit /etc/default/grub instead, followed by sudo update-grub.

Ref: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[LIST]
[*] The main menu file, /boot/grub/grub.cfg, is not meant to be edited, even by 'root'.
[*] grub.cfg is overwritten anytime there is a update, a kernel is added/removed, or the user runs update-grub
[/LIST]

---

### Post by WorMzy on 2010-07-11
Also, it's a bit late to say this now, but it's better to use gksu or gksudo rather than sudo for graphical applications. There generally aren't that many problems that sprout from using sudo instead, but it's a good habit to use the right commands.

---

