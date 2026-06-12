---
title: "How do I load a .ko driver file in 8.04?"
date: 2009-07-22
forum: General Help
---

### Post by webgrunt on 2009-07-22
I'm supposed to test a .ko file.  It's a driver, and I need to see whether or not it loads in Ubuntu 8.04 Hardy Heron.  I know how to copy the file to the HH desktop and how to open the terminal, and that's it.  Can someone kindly explain to me how I can load a .ko driver file?

Thanks.

---

### Post by jerrrys on 2009-07-23
never did it so can't explain it, but can point you to this

[http://www.google.com/search?q=how+to+install+.ko+driver+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=how+to+install+.ko+driver+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Ayuthia on 2009-07-23
If you are just testing the .ko file, you should be able to use:
```
sudo insmod name.ko
```Replace name with the actual name.

---

### Post by webgrunt on 2009-07-23
Thanks gigs!!

---

