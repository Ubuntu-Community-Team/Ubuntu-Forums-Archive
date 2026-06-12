---
title: "Multi Screen Help"
date: 2011-09-08
forum: General Help
---

### Post by GadgetHammer on 2011-09-08
[FONT=Times New Roman][SIZE=3]Well I will start from the beginning. A while back I started using Linux, and simply dual booting my machine to Ubuntu and XP. But I have recently built a new machine that is much more powerful, I have XP on it but I want to go to completely Linux. I have already found ways to run ever program I use on Ubuntu, but I am having an issue with my Graphic Cards. (Sorry if this post is lengthy, I am going to try to include all the info I can)[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]I have a quad screen set up, between 2 video cards (ATI Radon HD 4550, and NVIDIA GeForce 6200) The ATI Card is my main card, and it runs the center screen, and the one above it. The NVIDIA card runs the 2 side screens. [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]The issue is I can get one card to run dual screens, But I cant get both to run quad screens. I searched the issue online, and found I need to edit xorg.conf. I followed the instructions and restarted and it wouldn’t load up the GUI, So I booted up to a live disk and fixed it what I did.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have gone threw like 20 tutorials on how to fix this and either it doesn’t load the GUI anymore or it don’t do anything at all. Ubuntu finds the drivers, and if I install one I have to set it up in my bios to boot to that video card, but that card works fine with dual screens.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]All I want is to have my quad screens like I do in XP, if I can resolve that I can stop using XP all together. I am like 98% sure that its something with the xorg.conf.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Please can someone just help me with this issue, Its probably something simple and stupid to fix, I just don’t know how. ](*,)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Please help me, save me from Windows XP.[/SIZE][/FONT]

---

### Post by zero2xiii on 2011-09-08
Dont wanna be the barrer of bad news.

But I am not sure that you can run ATI and NVIDIA drivers on the same machine at the same time...

However, how are you setting up the screens? With the built in screen manager? Or the driver tools?

Cherz

---

### Post by GadgetHammer on 2011-09-08
I am useing the built in screen manager.  
 
And if your right the only way i will be able to use both cards is to replace one of them with the same brand card,  Right?

---

### Post by sanderd17 on 2011-09-08
> **GadgetHammer said:**
> I am useing the built in screen manager.  
 
And if your right the only way i will be able to use both cards is to replace one of them with the same brand card,  Right?

[s]Or use a card with two exits.[/s] Sorry, you already have such a card.

I've just done some things on Arch, and I noticed that installing the proprietary nvidia drivers conflicted with the ati drivers. So that certainly won't work, but maybe the nouveau drivers will work together with the ati drivers.

---

### Post by GadgetHammer on 2011-09-08
I will try the nouveau drivers tonight when i get home,  I will post what the results are.
 
at this point I may just bite the bullet and replace the NVIDIA card with a ATI one.

---

### Post by zero2xiii on 2011-09-09
> at this point I may just bite the bullet and replace the NVIDIA card with a ATI one.

Auhm sure. That is your decision. But I found that Nvidia is beter supported under linux than ATI. (although that was some time ago, little more than a year, may have changed).

But in short, yes. You are going to need two of the same vendor's cards. Not needed to be the EXACT same card. But deffenitly same make.

Good luck

---

