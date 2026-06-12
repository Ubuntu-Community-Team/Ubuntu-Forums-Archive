---
title: "I need help in recovering my lost OS mac OS"
date: 2011-12-11
forum: General Help
---

### Post by sekacorn on 2011-12-11
Hello

i recently installed Ubuntu 11.10 on my mac book pro but i erased my Hard disk accidentally.i have tried using testdisk to  recover it but every time i find the partition and i restart my ubuntu 11.10 its gone then i have to install it again. Can somebody help me recover Mac OS and its file using testdisk. i need to recover the partion and its files

here is  a screenshot of my hard disk using gpartiont disk
[IMG]http://i613.photobucket.com/albums/tt213/sekacorn/Clll/Screenshotat2011-12-11225524.png[/IMG]

---

### Post by gennatolls on 2011-12-11
You can try scalpel to recover your files

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Make sure you backup in the future. I think we've all been through this at some point. Best of luck

---

### Post by sekacorn on 2011-12-12
i have used the test disk option to recover the Mac OS i found the mac OS but i can't recover it. 
this is the screen shot of it'
[IMG]http://i613.photobucket.com/albums/tt213/sekacorn/Screenshotat2011-12-12160300.png[/IMG]

and this is what i get when press enter
[IMG]http://i613.photobucket.com/albums/tt213/sekacorn/Screenshotat2011-12-12155608.png[/IMG]

---

### Post by sekacorn on 2011-12-12
i have found out the problem . i didn't select it. it turns out that you have to press the left arrow key then it will turn green and then press enter or return

---

### Post by oldtimer7777 on 2011-12-12
> **sekacorn said:**
> i have found out the problem . i didn't select it. it turns out that you have to press the left arrow key then it will turn green and then press enter or return

Awesome.. Good job there!!! 

:popcorn:

---

### Post by sekacorn on 2011-12-13
i have successfully recoverd the partition but there is another problem. i can't boot into it

---

### Post by oldfred on 2011-12-13
I do not know Macs. But they use gpt and efi which would not have a bios_grub which is if booting in BIOS mode not efi. But Apples efi is not quite the same as UEFI and grub has not fully gotten UEFI to work in all cases.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

---

### Post by Quackers on 2011-12-13
Sorry, not much help for you but it may be an idea to post in the Apple Users section of the forum.
Good luck.

---

