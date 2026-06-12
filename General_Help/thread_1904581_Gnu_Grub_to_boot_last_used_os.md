---
title: "Gnu Grub to boot last used os"
date: 2012-01-05
forum: General Help
---

### Post by pigmentty on 2012-01-05
Hello, i have been using ubuntu for a few months now, and it has been hard learning things on my own, i like to code some in windows, mostly for fun.

One thing i would like is to modify the settings in gnu grub to boot the last used os, can anyone help me? I tried to read the manual, but lets just say it's big, very big, and the few instructions i found related to what i wanted turned out useless.

---

### Post by Basher101 on 2012-01-05
> **pigmentty said:**
> Hello, i have been using ubuntu for a few months now, and it has been hard learning things on my own, i like to code some in windows, mostly for fun.

One thing i would like is to modify the settings in gnu grub to boot the last used os, can anyone help me? I tried to read the manual, but lets just say it's big, very big, and the few instructions i found related to what i wanted turned out useless.

as far as i know there is no option to boot the "last used" os. But i can show you how to edit the grub configuration file on what the default OS is to be booted. Important here is how many grub entries you have, by default it should look like this for a normal dualboot:```
Linux headers
Linux headers (recovery)
Memtest
Memtest 86
/dev/sda Windows
```
making it a total of 5 entries, starting at 0. Thus the last entry, in this example windows, would have the entry number 4. Now once we are booted into ubuntu you can open a terminal and type ```
gksu gedit /etc/default/grub
``` to open the configuration file. There you edit the line that says ```
GRUB_Default=0
``` there you change the number to the entry number of which OS you would like to boot by default (change it to 4 if you want windows like shown in the example). You can also edit the line ```
GRUB_TIMEOUT=10
``` on how many seconds the Grub bootloader is supposed to "wait" for input before loading the default OS.

After you are done with the changes, save the settings.

type the command in the terminal ```
sudo update-grub
``` for the changes to take effect.

done




regards

---

### Post by WorMzy on 2012-01-05
Ubuntu uses Grub 2, so this should work for you: [https://wiki.archlinux.org/index.php/GRUB2#Recall_previous_entry](https://wiki.archlinux.org/index.php/GRUB2#Recall_previous_entry)

---

### Post by mcduck on 2012-01-05
Edit /etc/default/grub, and set the GRUB_DEFAULT to "saved" and GRUB_SAVEDEFAULT to "true". Save the file and run "sudo update-grub". It will now always default to the last used option.

---

