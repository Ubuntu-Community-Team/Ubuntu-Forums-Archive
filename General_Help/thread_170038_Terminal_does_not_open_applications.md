---
title: "Terminal does not open applications"
date: 2006-05-03
forum: General Help
---

### Post by till on 2006-05-03
Dear all,

I am trying to change my default OS in Grub from Ubuntu to XP using the following line in Terminal:

sudo gedit /boot/grub/menu.lst

However, after being prompted for my password and entering it, nothing happens - the text editor does not open.

How can I fix this and open the text editor as root?

Thank you very much for your help,
Till

---

### Post by enopepsoo on 2006-05-03
did you try ```
sudo gedit
``` or ```
sudo nano /etc/grub/menu.lst
```?
nano is a good thing to know how to use anyways, you can't open grub through a secure shell.

---

### Post by MasonM on 2006-05-03
Hmmm, not sure unless you're mistyping something. I just tried it "sudo gedit /boot/grub/menu.lst" and it worked fine.

---

### Post by till on 2006-05-04
Thank you very much for your hints. Just tried these commands. Nothing works. Terminal does not open any application.

Has anyone an idea how to force Terminal to open applications?

Thank you very much!

---

