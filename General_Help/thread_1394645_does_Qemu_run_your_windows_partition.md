---
title: "does Qemu run your windows partition?"
date: 2010-01-30
forum: General Help
---

### Post by willro on 2010-01-30
well just wondering, cause i wanted to run sketchup. and gamemaker without having to worry bout rebooting into windows.

---

### Post by mushwars on 2010-01-30
Not even sure what that is, but if the program runs on linux or even if not install it with wine then ln -s the files you need in your MOUNTED windows partition then load them in the program

---

### Post by susanw on 2010-03-01
Hello,

Sketchup should run fine in wine, just got it working this weekend after a few registry tweaks. Not sure if you're still looking into this issue but thought I'd add my twopennies worth. Currently looking into Qemu myself for different piece of software I can't figure out how to run in wine even.

Good luck with it.

---

### Post by bodhi.zazen on 2010-03-01
In theory, qemu will run your windows partition. In practice it is a bit tricky and is not advised.

In a nutshell, your windows install will not like booting with qemu as your hardware will have changed.

IMO qemu is slow and I think you will find virtualbox is faster.

Either way I suggest you use a virtual hard drive unless you understand how qemu and windows work.

If you must, this is one method to boot your physical partition :

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

---

