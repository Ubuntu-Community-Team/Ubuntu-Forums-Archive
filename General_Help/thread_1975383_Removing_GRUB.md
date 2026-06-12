---
title: "Removing GRUB"
date: 2012-05-07
forum: General Help
---

### Post by cubemike99 on 2012-05-07
Hello. I was hoping for some advice on the removal of GRUB from my MBR. I've come up from a strategy that may work, but I want some confirmation before I try it.

My school rents out laptops to all its students. Wanting to experiment with linux, I put Ubuntu on it. Apparently, our IT guy doesn't know how to format, so unless I manage to remove GRUB, I'm going to be charged for a new hard drive :mad:. So, my plan is this: since all the laptops are identical, can I copy a clean boot sector (first 512 bytes) from someone who doesn't have linux, and then simply put it onto my hardrive? Would this give me a MBR without GRUB that will boot Windows? Or, would it be easier to simply use something like Rescatux? Thanks for the help.

---

### Post by zvacet on 2012-05-08
If you have Windows on that comp first do [this.]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe") Afte that you can delete ubuntu partition.Of course you can see [here]("http://members.iinet.net.au/~herman546/p18.html") for other solutions.

---

