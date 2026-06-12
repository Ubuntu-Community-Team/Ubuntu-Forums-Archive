---
title: "Ubuntu won't shut down"
date: 2010-06-22
forum: General Help
---

### Post by __jack__ on 2010-06-22
I've just started using new Ubuntu desktop edition 10.04 and I have a problem. When I try to shut down the system it just wont do it. The logo ubuntu and 5 dots stays there forewer.

What can I do?

---

### Post by a-user on 2010-06-22
i guess nothing cause there are allready many ppl with the same issue. it is kernel related. but of course you cuold be lucky and your case is different with a solution to this problem.

try to use suspend or hibernate and write if it also does not shut down, meaning it does preapre for it but actually does not power off.

if so, then you are in the same situation as me and some others. and as long as they don't change the kernel you wont see a fix for that.

edit: i used a newer kernel 2.6.33 or newer to avoid this. you can try using a mainline kernel but the mainline kernels miss some patches like ureadahead support and apparmor. if you do not needed that you can use them. if you are more expert you can compile a new kernel with the patches (i never found the patches for apparmor though).

---

### Post by __jack__ on 2010-06-22
No neither of them isn't working. When I put it to hibernate, nothing happens, but when I put it to suspend, screen becomes black but I cant rewoke it anymore.

It is interesting that all older versions of Ubuntu worked perfect for me on the same notebook. Only this one isn't working.

---

### Post by a-user on 2010-06-22
although i find it uncommon that hibernate does not show the same behaviour as suspend in your case i think it is what i first guessed. hence no solution with current kernel.

and yes, this worked with kernel 2.6.31. it is only an issue with kernel 2.6.32 (dunno if it also happens with the originial kernel or only with the ubuntu version).

so if you need to fix that search for my thread where i psoted this same issue with suspend and hibernate. there i posted links to guides how to compile a new kernel with ureadahead support. or you can use a precompiled mainline kernel.

---

### Post by Smart Viking on 2010-06-22
Um, i have no idea about this problem and how to fix it, but what happens when you try to shut down from the terminal with this command:

```
sudo shutdown -h now

```I hope this helps somehow. :)

---

### Post by __jack__ on 2010-06-22
No writing a command in terminal doesnt do it either.

---

