---
title: "GRUB update lockup"
date: 2010-05-06
forum: General Help
---

### Post by ninja togo on 2010-05-06
My computer has seemed to freeze the update window labeled, "Debconf on ubuntu", it was at the screen that said, "Configuring Grub-pc". There was a checkbox that said, "continue without installing Grub". 

Now being a linux noob I decided to tick the checkbox, seeing as it would not respond to clicking forward with the checkbox unchecked.

My question is: is that supposed to happen forcing the user to go without the update? I've been using Wubi, if that matters at all.

I'm scared to restart my PC as it may not boot back up properly. Am I safe?

---

### Post by swappa on 2010-05-07
Got the same problem. Both in 9.10 and 10.04

---

### Post by dino99 on 2010-05-07
if you want to test ubuntu, either install directly on its own partitions or install virtualbox with windows, then install ubuntu into virtualbox

wubi= ubuntu into a windoz file :lolflag: something strange

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by DiagonalArg on 2010-05-29
I got the same problem, in 10.04.  Installed XP, then installed Wubi.  Everything went fine until I updated Ubuntu.  Then I was unable to install grub.  Right now, afraid to reboot my computer ...

---

### Post by HKei on 2010-05-29
Well, if nothing else works, you should still have BIOS or something similar hardcoded in your motherboard... so, you should still be able to boot from a CD or similar.

---

### Post by ninja togo on 2010-05-30
Don't worry guys, I fixed this with a quick reinstall, after moving all my documents and such to my portable hard drive.

---

### Post by Spr0k3t on 2010-05-30
I don't think there is a way to install grub/grub2 using wubi.  I could be wrong though...

---

