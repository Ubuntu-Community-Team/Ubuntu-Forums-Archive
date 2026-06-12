---
title: "where is /boot/grub/menu.lst?"
date: 2009-12-03
forum: General Help
---

### Post by waitn2drive on 2009-12-03
I have just installed Ubuntu 9.10 on my laptop after not having Ubuntu for a while. I have it installed to dual boot with Windows Vista and want to set Vista as the default Operating System to boot when the computer is turned on. I went to the terminal and put in the following correct comman for Ubuntu 9.08 "sudo gedit /boot/grub/menu.lst" and then open the gedit. To my surprise, it was just a blank document with nothing in it. I then navigated to /boot/grub/ and looked for menu.lst where I found nothing, is there a new file in Ubuntu 9.1 like the file in 9.08 to edit grub loader? Please inform me as I wish to edit the amount of time the countdown timer is for and change my default os.

Thank you,
              waitn2drive

---

### Post by Cheesemill on 2009-12-03
[LEFT]9.10 uses the new version of grub which doesn't use menu.lst anymore.

See here for more info:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[/LEFT]

---

### Post by efflandt on 2009-12-03
See /etc/default/grub, the files in /etc/grub.d, then web search grub2.

---

