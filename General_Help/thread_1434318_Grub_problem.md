---
title: "Grub problem"
date: 2010-03-20
forum: General Help
---

### Post by sharksaw40 on 2010-03-20
Hi

I quite new to Ubuntu and I used to have Grub 2. When Ubuntu updated the next time I turned on my laptop and selected Ubuntu from the windows boot menu grub 1 appears instead of Grub 2. I have tried to load Ubuntu by entering the boot command but an error comes up how do I get Grub 2 back without a Ubuntu live CD.

Thanks

---

### Post by darolu on 2010-03-20
Remember that "Grub 2" is really 1.97 beta right now.

You should find all you need to fix it here: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Edit: with no Live CD you may want to read this one too: [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

---

### Post by karthick ayyapillai on 2010-03-20
Hi
I am using Grub 1.97~4 Beta version wit h ubuntu 9.10 karmic kola.
I got an update from repository and after the update it gave me a new image linux kernel 2.6.31.20-20. At the final stage of the update it gave an error message that the image cant be updated. I tried to run sudo update-grub in terminal it gave an error that 
etc/default/grub: Permission denied(1). Then after checking all the files one by one in etc/default/grub and usr/boot/grub/grub.cfg .I tried again no use after rebooting through terminal I ran the command sudo grub-mkconfig -o /boot/grub/grub.cfg .I got an error telling that etc/default/grub:9 :not found
I tried with root previlages as well same thing is happening .
If anyone has the same problem and have any solution please let me knw thanks for the help.

---

