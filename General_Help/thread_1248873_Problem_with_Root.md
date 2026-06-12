---
title: "Problem with Root"
date: 2009-08-24
forum: General Help
---

### Post by jtrulen on 2009-08-24
I was recently following a tutorial to build a web server ( keep in mind that I am quite new to Linux as a whole ) and it told me to type in:    sudo passwd root

Now that I have had time to research it a bit more, I found that this is a bad thing to have done. I have also tried to reset it so when you type in sudo before a command it asks you for your password again. But I have yet to find a way to do this.

I have tried using: sudo passwd -l root, and:sudo usermod -p '!' root. However they did nothing. Still when I type in sudo *command* it never asks for a root password. 

If anyone can help, that would be greatly appreciated.

---

### Post by lisati on 2009-08-24
Presumably you have already the info at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jtrulen on 2009-08-24
Thanks lisati. I did read that page a bit, but I guess I didn't read down far enough in my haste.

---

