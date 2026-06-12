---
title: "Ubuntu new user problems . ."
date: 2009-08-08
forum: General Help
---

### Post by phuchungbhutia on 2009-08-08
I have two drives one is sata and another pata and . . I have win xp in sata and i installed ubuntu in the other today . . But i couldnt see ubuntu detect sata drive even while installing and so there is no bootloader either . . One more thing is that i didnt partition swap so could that be any problem but i dont think so . . As it didnt show any other drive i dont think so . .  Plus it takes time to start up the ubuntu os . . Now i have to change boot drive priority everytime i need to change the os i want to use . .   and if swap does help . . How do i install bootloader plus create swap . .

---

### Post by jrothwell97 on 2009-08-08
First of all, this is in the wrong forum (it should be in Absolute Beginner Talk.)

Second, you probably need to configure GRUB to allow you to boot (or *chainload*, in this case) from the SATA drive on which XP is installed. Please post the contents of /etc/grub/menu.lst (or, if that doesn't exist, /boot/grub/grub.cfg) so we can find out what's wrong and how to get Windows working again.

Third, you really should create a swap partition, but Linux is also OK with a swap file. (You can probably get away without either if you have enough RAM.) If you decide you do need swap space, instructions can be found [here](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?) (judging by the fact you know the difference between SATA and PATA, I'm guessing you have enough expertise to follow those instructions.)

---

