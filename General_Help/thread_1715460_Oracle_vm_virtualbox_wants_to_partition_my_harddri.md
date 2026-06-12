---
title: "Oracle vm virtualbox wants to partition my harddrive. Good?"
date: 2011-03-27
forum: General Help
---

### Post by Azaz on 2011-03-27
Im trying to run Arch Linux off Oracle vm virtualbox and everything going fine until It wants to wipe my entire hard drive. To be fully honest im afraid to touch it. I feel like it might bite my finger off if I poke at it in my usual way (first time ever using VM) so I was wondering if anyone has any tips or advice for me. Maybe someone elce has tryed this before and can tell me my computer wont explode when I partition. (I know it wont but I only have 1 computer and afraid to ruin it with my "experiments" cant afford a new one) I think because its VM it will only partition the space I set for it when I started the VM box. Just looking to be safe before I try it.** **

I know this is now the right forum but Iv had nothing but good advice from this community. Thanks for all the help in the past. 

Azaz

---

### Post by Vaphell on 2011-03-27
i think it wants to wipe the harddrive it sees, which would be the fake filesystem you create during setup. Does it say what is the size of the drive it wants to format?

---

### Post by bobthebaritone on 2011-03-27
Make sure you know exactly how your drives translate to what *nix wants to see. Usually, it will be only trying to format the virtual disk you have created for the guest OS

Backup lots and often!

Cheers,

Bob

---

### Post by jwbrase on 2011-03-27
Unless you actually told VirtualBox to use your computer's hard drive as the hard drive for the virtual machine, all it will do is wipe the hard drive image you created for the virtual machine, which should be all right since that is probably blank to start with anyways. 

If you set it up to use your computer's hard drive as the virtual machine's hard drive, then you could end up in trouble.

Make sure it's not using your computer's hard drive as the drive for the virtual machine, and then, once you're sure it's not, everything should be safe.

---

### Post by Azaz on 2011-03-27
thanks guys :) no problems it only partitioned the set amount of space I told it to at the start.

---

