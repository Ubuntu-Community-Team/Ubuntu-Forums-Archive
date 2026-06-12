---
title: "Grub Loader Order"
date: 2009-09-28
forum: General Help
---

### Post by daithi81 on 2009-09-28
Hello, I have Googled this query and have found various solutions but none of them work. I simply want to change the default load option on Grub from Ubuntu to Vista. When I attempt to edit menu.list and change default=0 to the relevant number, I can't as the file itself seems to be read-only and I am told I cannot alter it as I am not the owner. Marvelous. I am the admin of this pc so what is the story?

---

### Post by Bucky Ball on 2009-09-28
```
sudo nano /boot/grub/menu.lst
```

---

### Post by daithi81 on 2009-09-28
Thanks!

---

### Post by Bucky Ball on 2009-09-28
Pleasure.

sudo = super user do

It makes you root for the next command.

---

