---
title: "First step on a long road!!"
date: 2006-03-29
forum: General Help
---

### Post by Big-B on 2006-03-29
Hello all, 
  Time to venture away from M$ for a change, i began my adventure last night and BAM!! right into a wall with a problem.  Burned iso file to disk, loaded onto spare comp i have laying around.  First partitioning and loading goes smoothly, ejects the cd, ok, so far so good.  Now it starts finallizing other modules and setups i assume, gets to where it is configuring "xserver-xorg".  The progress meter sits on 71% and that is it.  freezes up.  Seeing as how this is my first attempt at leaning linux, i am a bit intimidated, can't even dos commands to try and figure something out.  I have read through a few forums, and i'm gathering if has something to do with the video i think.  I have a few old video cards laying about, should i try one of those?  maybe it doesn't like the driver its trying to formulate??  i'm at a loss everyone, any help would be great!!  thanks in advance.

---

### Post by ispmarin on 2006-03-29
Could you post the hardware configuration? What is the manufacturer of the motherboard and the video board? Are you trying to install witch version of ubuntu?

---

### Post by Big-B on 2006-03-29
more info would definitely help, mobo is a chaintech, nothing fancy not even onboard video, amd 1.5ghz, 512 memory, 80GB HDa, the video card i will have to look at, it is a few years old, and not an off the top of my head company.  That is why i was thinking of switching out the card, i have an old nvidia tnt card that works fine.  I can post to the hardware by the way.
Also, it's Ubuntu, 5.10 the GNOME setup.

---

### Post by jbennett on 2006-03-29
[QUOTE=Big-B]more info would definitely help, mobo is a chaintech, nothing fancy not even onboard video, amd 1.5ghz, 512 memory, 80GB HDa, the video card i will have to look at, it is a few years old, and not an off the top of my head company.  That is why i was thinking of switching out the card, i have an old nvidia tnt card that works fine.  I can post to the hardware by the way.
Also, it's Ubuntu, 5.10 the GNOME setup.[/QUOTE]

I would definitely try swapping the video cards and attempting the installation with the nVidia card you have.  Historically, nVidia cards have been much more cooperative with Ubuntu (or maybe its the other way around :) )

Let us know how it turns out.

---

### Post by Big-B on 2006-03-30
TADA!!!  i tried to load again, this time with an "official", not iso burned ubuntu disk, just incase it had something to do with the burn.  Same outcome, so swapped out video card, the one i took out was a diamond video card?  I kinda remember them, had the voodoo 3d gpu's.  Put an nvidia tnt2 card, and it loaded great.  My advice, stay with manstream video cards!  Thanks for the responses!

---

### Post by rcmiv on 2006-03-30
[QUOTE=Big-B]Hello all, 
  Time to venture away from M$ for a change, i began my adventure last night and BAM!! right into a wall with a problem.[/QUOTE]

I am happy that you got your problem worked out.

This strikes me as being an appropriately educational "First step on a long road," and I would plan for several more just like it.  I like the fact that even ubuntu usually has some cost of entry.  And it certainly seems that you're up for it.

I've been using desktop linux since '96 with Caldera (and no, the Santa Cruz Operation hasn't always been evil, though it clearly became so...), and I can't begin to relate the number of steps there have been for me along the road like the first one you just took.

But that's what makes it fun.  Ubuntu has made computing in general more fun for me than anything since I began digging under the hood of the Amiga workbench.  It's worth the effort to configure and customize.  I am doing things with it that are unimagineable or prohibitively expensive in windows; xgl/compiz, iptables, and even simple metacity theming come to mind as examples.

So good luck! And remember that even longest journey begins with but a single step (and usually something like sudo vim /etc/apt/sources.list)

-rcmiv

---

