---
title: "BURG / grub2 update problem"
date: 2012-06-28
forum: General Help
---

### Post by sks24 on 2012-06-28
First off, my apologies in advance for not providing the requisite level of detail with this post.  

Here's what happened: during a system update, I saw a pop-up box asking me something about whether I wanted to use or update or configure - I'm not exactly sure - BURG or grub2.  I simply said OK to the default choice.  This machine was, in fact, running BURG.  After the update, I couldn't boot either OS.  I first tried the SGD boot disk and tried fixing grub2, then fixing the Windows boot. Then I tried the Dell disk which came with the tower.  No luck.  Said some files were missing.  So now there's a problem using the disks to rebuild Windows.  

But here's my question: have I provided enough information for someone to tell me what I should have chosen in that dialogue box?  If so, then which choice should I be making when these updates occur?  I'm all but certain that that is the origin of the problem.  

This was an old 32bit Dell tower running 12.04, and again, I'm sorry for the lack of detail here: I should have been more careful, and, in the future, I will be.  My main concern is the BURG installations I have on a couple of my friend's machines:
is there something I can do to insure that they will not be faced with the same choice in terms of that BURG/grub2 update choice?

Thanks in advance,
Scott

---

### Post by dcstar on 2012-06-30
> **sks24 said:**
> 
.......
is there something I can do to insure that they will not be faced with the same choice in terms of that BURG/grub2 update choice?

Thanks in advance,
Scott

If you are using BURG then uninstall Grub and you won't inadvertently install it over the top of BURG when a Grub update arrives.

---

### Post by sks24 on 2012-06-30
Excellent.  Thank you David.  Removing Grub would never have occurred to me, and it would seem that doing so could not but solve this particular problem.

I'll leave this open in case I can't determine how to do this, and need to ask another question or two.

Again, thanks,
Scott

---

