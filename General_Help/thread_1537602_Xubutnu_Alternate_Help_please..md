---
title: "Xubutnu Alternate Help please."
date: 2010-07-23
forum: General Help
---

### Post by bluealiens on 2010-07-23
I just burned a Xubuntu Alternate CD 10.04. I popped it in the laptop. I selected install then... strange. It was unreadable. I pressed the up arror and a red blob moved up so I  figured something was happening. I wish i could explain better. The same happened with lubuntu (i put the files on HDD and told grub to load from them). I used old xubuntu and it worked! My PC is an old Acer Apire 1350. 192mb ram, 700mhz processor)

Please help
      From
            BlueAliens

---

### Post by robsoles on 2010-07-24
Hi bluealiens.

Can you make yourself a booting USB stick from xubuntu or lubuntu source iso to try to boot from or does this laptop disallow booting from such removable media?

It seems fairly advanced to me, to be copying files to your hard drive and then making grub use them to boot from, maybe that in itself is 'falling down' and maybe it is that the graphics adapter in use on your laptop was overlooked when they made the generic drivers for the LiveCD - the nearer to the LiveCD (that is, like a USB created from an ISO of a LiveCD) you can boot from the easier it will be to get help with it in any case!

---

### Post by robsoles on 2010-07-24
OK, I re-read your original post and I think my first response is a bit rubbish - I nearly deleted it but then I decided I would post a new reply and leave my first one there to remind me not to post in such a hurry sometimes!

If you use a text mode to install the OS and then it boots and you get this unreadable display we can maybe fix it with the manufacturer's driver for your graphics controller in that laptop.

Please tell me for sure what graphics controller that  laptop is using - there is an Ok chance of installing it via the  terminal.

Next time you are looking at the red blotchy display please press  [CTRL]+[ALT]+[F4] and confirm for me that you can read the display in  the terminal login prompt that (hopefully) appears on your display - we  are going to need this to get your graphics drivers working.

---

