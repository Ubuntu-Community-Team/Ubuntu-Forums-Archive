---
title: "Multiple monitor tags in upper left corner wont go away"
date: 2010-06-24
forum: General Help
---

### Post by Scolecite on 2010-06-24
I have my laptop connected to an external monitor and in the upper left hand of both screens is an identifier that wont go away and is blocking my view. On my laptop it says "Laptop" and then "Dell 20"" on my secondary display. 

I just want to get rid of these labels. I have checked and unchecked "Show monitors in panel" and that seems to be my only option. 
Thanks!

---

### Post by dcstar on 2010-06-25
> **Scolecite said:**
> I have my laptop connected to an external monitor and in the upper left hand of both screens is an identifier that wont go away and is blocking my view. On my laptop it says "Laptop" and then "Dell 20"" on my secondary display. 

I just want to get rid of these labels. I have checked and unchecked "Show monitors in panel" and that seems to be my only option. 
Thanks!

If you have Nvidia or ATI hardware drivers installed there may be a setting in their individual control programs.

---

### Post by bakinsoda on 2010-08-04
Did this ever get resolved?  I have the same issue.  @dcstar???

---

### Post by SimenMM on 2010-08-20
I have this problem as well. I've googled it, but can't find any solution. It makes me wish I'd never upgraded, all it does is block useful information. Now that the close window tabs have been moved to the left, I can't even use the drop-down menus in Firefox without unmaximizing it and moving the window. Worst. Update. Ever.

---

### Post by SimenMM on 2010-08-22
I may have stumbled upon a fix. I went into gconf-editor and edited the apps/metacity/general/button layout value to say menu:minimize,maximise,close , and afterward the tags were gone. I'm not sure if that's what removed them (and it sounds like magic), but gone they are.

---

### Post by bakinsoda on 2010-08-22
@SimenMM: Thanks for sharing your solution.  I confirm that it works.  The tags only show when the screen configuration program is active, and when we close it, the tags disappear.

---

