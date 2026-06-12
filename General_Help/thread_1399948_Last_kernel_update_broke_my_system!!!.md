---
title: "Last kernel update broke my system!!!"
date: 2010-02-06
forum: General Help
---

### Post by scu8a on 2010-02-06
Hello ,i upgraded my kernel to the latest version that being linux-image-2.6.31-19 and now when i start my linux box i get the grub shell. this problem happend once before but i only had to run the command:

sudo update-grub2

and everything turned back normal. now even though i run the command everytime i restart my linux i get the grub shell.
Anyone knows how to resolve this?
thnx

---

### Post by minws on 2010-02-06
Hi

are booting with wubi?

---

### Post by scu8a on 2010-02-07
yes i'm using wubi

---

### Post by mikeh244 on 2010-02-07
I had exactly the same problem. There were so many messages scrolling off the screen it was impossible to see the actual error message, but it just gives the GRUB prompt.
Manually bottinh kernel 19 also fails - I had to go back to 17.

Mikeh

---

### Post by Silvertones on 2010-02-07
You need to replace your wubildr file in  C:/wubildr in Windows. I supplied it here.
[http://ubuntuforums.org/showthread.php?t=1398910](http://ubuntuforums.org/showthread.php?t=1398910)

---

### Post by Silvertones on 2010-02-07
did this not work?

---

