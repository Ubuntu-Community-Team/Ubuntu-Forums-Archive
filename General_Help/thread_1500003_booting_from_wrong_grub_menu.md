---
title: "booting from wrong grub menu"
date: 2010-06-02
forum: General Help
---

### Post by raysa on 2010-06-02
I have two versions of Ubuntu on my computer - 10.04 and an earlier one that i no longer use. I'd like to free up the space that the old partition is taking, but the computer boots from the grub menu.lst of that old version. How can I make the boot process use the menu.lst in the 10.04 partition?

Actually, where is the boot process situated anyway and how can you get at it?

Thanks,
Ray

---

### Post by arrange on 2010-06-02
Do you want to keep the old (Legacy) Grub or use Grub2 instead?
Are you sure that the old *menu.lst* is used? Could you provide the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") (just to be sure)? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by wojox on 2010-06-02
I'd install Grub2 from the LiveCD [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by raysa on 2010-06-03
I did a silly thing. I erased the partition where the old installation was, thinking that the booting process would find and use the remaining 10.04 partition. Oops! the computer wouldn't boot at all - I suppose it couldn't find the grub it was looking for and didn't know where to look for the good one.

I had a CD installation of Ubuntu 10.04 netbook version handy (from installing it on another machine) so I installed that (into the partition where the old installation was) to get me going.

So now I have the 10.04 desktop version - the one I want - on one partition and the netbook version, which I don't want, on another partition. But the computer still boots from the unwanted installation (clearly verified by boot_info_script).

How can I point the computer's initial boot process to the desired partition?

Thanks, Ray

---

