---
title: "Grub bootloader help!!!"
date: 2010-01-23
forum: General Help
---

### Post by katokato on 2010-01-23
i did an update then i restarted my computer (i have windows vista and windows 7 and ubuntu triple booted), and my grub bootloader takes me to a command line screen, here is what it says:

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions]

sh:grub>_

---------------------------

helllp me how do i fix this error and boot into an operating system and fix grub? I have very important files on my computer! Sorry if i sound noobish i just started using ubuntu!

i do not use wubi

------------------Thanks

---

### Post by katokato on 2010-01-23
oh and here is my boot info (attachments)

---

### Post by 73ckn797 on 2010-01-23
Check out this info: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Sections 13 and/or 16 should help. It deals with restoring the grub boot loader.

---

### Post by oldfred on 2010-01-23
Your listing of grub.cfg does not look complete as it does not show any menu items.

Try this which I just copied from meierfra

Type this at the "sh: grub> " prompt:

```
search -f --set /vmlinuz
probe  -u --set=UUID $root
linux /vmlinuz root=UUID=$UUID ro
initrd /initrd.img
boot
```

This should boot you into Ubuntu.
Open a terminal in Ubuntu and run

```
sudo update-grub

```

---

### Post by katokato on 2010-01-23
search -f --set /vmlinuz
probe  -u --set=UUID $root
linux /vmlinuz root=UUID=$UUID ro
initrd /initrd.img
boot

that worked i could get into ubuntu, but sudo update-grub didnt work

the command ran correctly, but when i restarted it still takes me to the prompt, any other ideas?

and also step 13 (of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)) didnt work

---------------thanks

---

### Post by Leppie on 2010-01-23
it actually looks like your grub did not install properly.
after booting into the system, try removing it and then reinstalling it:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common
```

---

### Post by katokato on 2010-01-23
THanks guys it worked i got to sucessfully boot into my winows oses, now i hope i dont mess up again, but if i do ill make sure to do the commands again: 
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common

thanks to: leppie, oldfred, and [73ckn797]("http://ubuntuforums.org/member.php?u=641480"). you guys have been a great help, just one more question, how do i raise ur rep levels or something alike?

---

