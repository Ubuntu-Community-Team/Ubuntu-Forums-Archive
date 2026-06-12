---
title: "Windows characters don't show up in Linux, and viceversa"
date: 2009-08-11
forum: General Help
---

### Post by valhar2000 on 2009-08-11
I have a strange problem that I have not been able to fix. Whenever I've googled it, I have found only pages that relate to a broadly similar problem that I don't actually have.

I have one computer running Windows Vista x64, another with Ubuntu and a laptop with Kubuntu. My problem is that some characters in filenames will sometimes show up well on 2 of the computers, but not on the other one.

This is not related to the forbidden characters in either Windows or Linux, because it happens to characters that are acceptable to both OS's; I think it's more to do with encoding.

For example, I have a file on the Ubuntu machine that contains the character "é". It appears just fine in both the Ubuntu and the Windows machines, but if I try to open it with my Kubuntu laptop, no applications can find it, and instead of seeing the character "é", the Kubuntu terminal shows the filename with 2 or 3 weird characters instead of the "é".

Fortunately, I can rename the file form the Kubuntu terminal, and then it works fine, but if I do that, the next time I try to access the file from the Windows machine Windows itself will see a weird character instead of the proper "é" character.

It happens mostly with vowels with accents on them, and occasionally some other character. Since I can rename the file whenever I notice it, I can eventually access them from any machine, but I really would like to figure out how to make them display correctly on all my computers.

Any help will be greatly appreciated.

---

### Post by Barafu Albino Cheetah on 2009-08-11
It is encoding, true.  Ubuntu uses UTF-8 as encoding for filenames, but what Windows uses depends on version and your language. You should play with mount options for your windows media.  Can't advise more because I didn't look how this is organised in Ubuntu myself.
You can always recognize utf-8 problem. If something reads utf-8, but don't know it is, it will see three weird characters, because utf-8 needs several bytes to keep a char.

---

