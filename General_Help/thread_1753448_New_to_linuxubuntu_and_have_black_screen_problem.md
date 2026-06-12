---
title: "New to linux/ubuntu and have black screen problem"
date: 2011-05-09
forum: General Help
---

### Post by zoi0sooB on 2011-05-09
This is what happned when i installed ubuntu while folloing this tutorial.

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

I asked /b/ how to fix it and somone said "turn on the Fu***** framebuffer. use vga=773 (iird) on the kernal command line. Look up how to do that"

I tried to find out but no luck.... The videocard is a EN 210 silent, if that helps....

Look at attached image if that will be of any help... I have no idea.

Thanks guys!

---

### Post by wilee-nilee on 2011-05-09
We are going to presume you have loaded what you need; a cli access or a desktop.

If you get a grub menu hit e (edit) use the arrow keys to add that vga=773 in the kernel line or change the one that is there. Look for the splash notation in the kernel line and insert vga=773 there leaving spaces or modify what vga is there.

You also may need nomodeset as well or instead with the same e=edit I am describing. nomodeset is alow graphics boot. 

The recovery kernel also takes you to a gui with a failsafe boot try that as well.

**Once you edit hit**
crtl-x 
to boot to a cli login and run
startx

---

### Post by zoi0sooB on 2011-05-09
Thanks for the fast reply, But i dont know how to do that.

When it boots up, all i see is the motherboard thing (press f12 to do whatever) and stuff, then when it boots it goes straight to that....
Sorry, im just a tad new...

---

### Post by wilee-nilee on 2011-05-09
> **famematt said:**
> Thanks for the fast reply, But i dont know how to do that.

When it boots up, all i see is the motherboard thing (press f12 to do whatever) and stuff, then when it boots it goes straight to that....
Sorry, im just a tad new...

Power on the computer immediately hold down the shift key it should get you to the grub menu to follow the instructions.

---

### Post by zoi0sooB on 2011-05-09
> **wilee-nilee said:**
> Power on the computer immediately hold down the shift key it should get you to the grub menu to follow the instructions.
Same issue... Sorry D:
Actually, I just noticed, the harddrive is going click click, click click, click click. on that screen, so right now im going to try installing ubuntu 10.10 just to make sure its not a hard drive issue or w/e

---

### Post by zoi0sooB on 2011-05-09
Okay, ubuntu 10.10 is installed so its obviously not a hard drive issue... ( i dont think )

---

