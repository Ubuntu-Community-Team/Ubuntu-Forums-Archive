---
title: "Dual monitor presentation with projector in ubuntu?"
date: 2009-09-28
forum: General Help
---

### Post by Javed_Ahamed on 2009-09-28
Hey guys,

I am trying to give a presentation with a powerpoint/code examples on ubuntu on a projector in class and was wondering how do I get dual monitors set up on ubuntu? I have an nvidia card but I want to mirror my desktops since I will not be able to look at the screen. Are there any programs that help with this as well?

Thank you in advance!:KS

---

### Post by scouser73 on 2009-09-28
Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Then go to **X Server Display Configuration** then set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by Javed_Ahamed on 2009-09-28
> **scouser73 said:**
> Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Then go to **X Server Display Configuration** then set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

thanks for the help scouser73, but there is no option to get a mirror display? Basically I want what shows up on my screen to also show up on the second screen. Thank you however, question still open!

---

### Post by i.r.id10t on 2009-09-28
The laptops I'm used to (Dells for hte most part) have a toggle switch to go from built in to external only to both - the both setting auto-mirrors, even in DOS.  Usually the blue fn key and either f5 or f8

---

### Post by scouser73 on 2009-09-28
> **Javed_Ahamed said:**
> thanks for the help scouser73, but there is no option to get a mirror display? Basically I want what shows up on my screen to also show up on the second screen. Thank you however, question still open!

Sorry, I should have been more clear, choose Separate X Screens.

---

### Post by Javed_Ahamed on 2009-09-28
Doesnt seperate x-windows just make seperate x windows? It doesnt mirror the actions of one window onto the other does it? I mean i have tried this before at home on a regular dual monitor setup and its basically like having two computers. Moving the mouse on one screen wouldnt move the mouse on the other?

---

### Post by bmdixon on 2009-10-17
I'm trying to do this too, did you figure it out?

---

