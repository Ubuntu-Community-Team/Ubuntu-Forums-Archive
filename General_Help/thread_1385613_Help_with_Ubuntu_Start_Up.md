---
title: "Help with Ubuntu Start Up"
date: 2010-01-19
forum: General Help
---

### Post by StephenKP on 2010-01-19
I have installed Ubuntu on my computer many times and never had a problem with installation or anything of the sort. Now I have burned the CD for my uncle to install it. (Ubuntu 8.04)  and we tried to install it several times. We removed GRUB from the main start up and reinstalled Windows NFTS and then put Ubuntu on it's own partition. (Reason for doing this was he installed it on C along with Windows. ) 

The problem were having is it doesn't boot into X or Gnome(I dunno what this part is called, just the GUI). it boots into terminal. No errors, just blank terminal. Anyway to fix this?

Computer Specs
 - 3 Gigs of Ram
 - (2)SLY Video Cards, 256mbs
 - AMD 3700+ Processor


Edit: I forgot to say it's dual booting windows XP.

---

### Post by victor.zamanian on 2010-01-19
If you removed GRUB *after* you installed Ubuntu, that might be weird, but I don't think that's what you did.

At any rate, I've had problems sometimes with new installations of Ubuntu, and they always seem related to burning the ISO to the CD at a rate that is too fast. When I burn the CD slower (about 4x), it seems to burn the image properly. This might not be the solution at all, just something you might try.

---

### Post by StephenKP on 2010-01-19
> **victor.zamanian said:**
> If you removed GRUB *after* you installed Ubuntu, that might be weird, but I don't think that's what you did.

At any rate, I've had problems sometimes with new installations of Ubuntu, and they always seem related to burning the ISO to the CD at a rate that is too fast. When I burn the CD slower (about 4x), it seems to burn the image properly. This might not be the solution at all, just something you might try.

Ahh my appologies. 

He installed it on his pc on his C:\ Drive. He did'nt want it there because it installed GRUB over NTFS. So we removed that problem. We then reinstalled Ubuntu on D:\ from Windows. 

Now GRUB is set up again but only when we select it from NTFS menu under Windows XP. 

I will try using the real CD I suppose, I have Ubuntu 9.04 so I might try that instead of 8.10 using the live CD. 

As for booting into Terminal, is there any commands that can be used after logging in to start the GUI version?

---

