---
title: "Hey can i install wubi on a another hardrive?"
date: 2010-05-02
forum: General Help
---

### Post by Usabent on 2010-05-02
My XP partion is C: and  1st HD. my  2nd Empty Hard drive part is F:/ Can i install wubi on the other hardrive using my c partuon?

---

### Post by Usabent on 2010-05-02
Bump :P

---

### Post by ford074 on 2010-05-02
[FONT="Arial"]No, I don't believe that this is possible with Wubi. Sorry.[/FONT]

---

### Post by bumanie on 2010-05-02
This is a slightly old tutorial, but the process should be much the same  - you're best to use lvpm to move a wubi install to a dedicated partition. Look [here ]("http://lubi.sourceforge.net/lvpm.html")

---

### Post by Usabent on 2010-05-02
It will take to long........ Eh ill install it on my C partion then..

---

### Post by oldfred on 2010-05-02
Wubi is fine for windows users who do not want to add partitions, use windows boot loader and have an extended test of Ubuntu. It assumes you only have one drive. But with two drives you have more choices.

If you are installing to a separate drive just do a full install. You install grub to the second drive's MBR and set BIOS to boot second drive. You can go back to the first windows drive at any time in BIOS as no changes are made to the windows drive.

I have not seen any instructions for Lucid but it is not much different from Karmic. With 2 drives you do need to check the advanced button on screen 8 of lucid to make sure grub is installed to sdb( if windows is sda).

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by Usabent on 2010-05-02
> **oldfred said:**
> Wubi is fine for windows users who do not want to add partitions, use windows boot loader and have an extended test of Ubuntu. It assumes you only have one drive. But with two drives you have more choices.

If you are installing to a separate drive just do a full install. You install grub to the second drive's MBR and set BIOS to boot second drive. You can go back to the first windows drive at any time in BIOS as no changes are made to the windows drive.

I have not seen any instructions for Lucid but it is not much different from Karmic. With 2 drives you do need to check the advanced button on screen 8 of lucid to make sure grub is installed to sdb( if windows is sda).

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Yea i tired dualbooting once i couldnt even get in to xp it just he underscore keeps blinking.

---

### Post by Usabent on 2010-05-02
Bum I SAY!

---

### Post by techunit on 2010-05-02
Also I believe that after you install wubi to your C: drive you can move it to a Harddrive elsewhere by following there instructions. [http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/](http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/)[]("http://www.pendrivelinux.com/move-wubi-ubuntu-install-to-an-external-usb-drive/")

---

### Post by razy60 on 2010-05-02
Hi, in your situation i would advise that you use virtualbox, it is similar to wubi in that it is a vm ware but much more usable and stable and if you dont like the OS you have installed you just delete and start again  plus you can install as many systems as you like then when you have had enough or dont want it any more just uninstall like any other program.

Raz

---

### Post by techunit on 2010-05-02
That's assuming his computer supports hardware visualization, without it he won't get the same experience as with wubi

---

