---
title: "Tablet features, can they work?"
date: 2012-07-15
forum: General Help
---

### Post by secuono on 2012-07-15
Hello, I am having ever growing and getting complicated issues with my WinXP laptop. If they continue, I want this PC to have Ubuntu on it. My desktop already does, but what always stopped me was that this is a tablet, so some features would not work or would be difficult for me to get working again...
Laptop is a Gateway Tablet CX210X. 
Discovered the other day, the pen will no longer 'write', but it does still moves the cursor. It won't left/right click or anything like that. 

Has anyone ever installed linux on my particular PC and gotten everything to work properly?

---

### Post by Favux on 2012-07-15
Hi secuono,

The short answer is yes.  The problem is not recently.

Your tablet PC uses the finepoint or fpit driver and it is no longer maintained.  Last commit to it was November last year I think.  So you would have to compile it.  Probably not a big deal.  I think I did it on Natty or Oneiric.

The issue is we haven't been able to get it to work.  I do have a .conf file for xorg.conf.d that should work.  And we know the setserial settings.  So we should be able to get it to work.

We've tried a couple of times with no luck.  Maybe made a simple configuration mistake somewhere or it could be a driver bug.

I did try to submit the .conf file to the driver maintainer just before he shut it down.  He needed verification it worked.  He'll accept new commits but they have to be tested and written by users.

Anyway the last time I remember it being setup and working, pen-wise, was Maverick or maybe Lucid.  At a minimum you should be able to set it up as a laptop.

---

