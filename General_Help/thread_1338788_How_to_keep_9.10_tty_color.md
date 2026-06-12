---
title: "How to keep 9.10 tty color?"
date: 2009-11-26
forum: General Help
---

### Post by shipofwar on 2009-11-26
I want change tty1-6 color to foreground color green background color black,so I input this line into ./bashrc
setterm -foreground green -background black -store
The color changed to green,but when I use man,ls --color,vi the color changed  to default white.
How can I keep the front color green?Some One said it need to change console.c,but I can't find it.
user1@notebook-laptop:/usr/src/linux-headers-2.6.31-15-generic/drivers/char$ find ./ -name *.c -print
Thanks
sorry for my poor english.

---

### Post by shipofwar on 2009-11-26
No one know?

---

### Post by raktarok on 2009-11-27
I followed what you did and it is working perfectly fine here. As soon as I login from the tty, the color changes automaticlly. Its running with vi and man too, so I don't know what is wrong there. Check vi's confifguration file to see if it is using separate color scheme, but I don't think this is the problem....maybe others can help you. anyway, thanks for the tip,now I have a cool looking tty console!

---

