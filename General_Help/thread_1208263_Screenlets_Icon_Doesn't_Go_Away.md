---
title: "Screenlets Icon Doesn't Go Away"
date: 2009-07-09
forum: General Help
---

### Post by nmaster on 2009-07-09
I recently installed Screenlets and but decided to uninstall it.  I removed it from "Add/Remove Applications," but the icon is still in the Notification Area of the upper panel.  I remove ~/.config/Screenlets and I checked in Synaptic that there are no screenlets packages installed.  

What's the deal?  Any solutions?

---

### Post by wojox on 2009-07-09
Right click and select Remove from panel.

---

### Post by jualin on 2009-07-09
Or go to System, Administration(or preferences, I am not on my ubuntu machine), Sessions and look for the "Screenlet" file and disable it.

---

### Post by nmaster on 2009-07-09
> **wojox said:**
> Right click and select Remove from panel.

that isn't an option. i can remove the entire Notification Area, but i don't want to do that.  i just want to remove the screenlets icon.

@jualin: im not sure what you are talking about.  i don't see any "sessions" under either preferences or administration.  could someone clarify?

---

### Post by wojox on 2009-07-09
System > Preferences > Sessions

---

### Post by nmaster on 2009-07-09
> **wojox said:**
> System > Preferences > Sessions

yeah like i said, this doesn't exist for me and i can't add it to the menu either.

---

### Post by PureLoneWolf on 2009-07-09
On Jaunty it is System/Preferences/Startup Applications

Find the Screenlets entry in there and get rid of it.

---

### Post by jualin on 2009-07-09
Sorry I wasn't in my ubuntu machine at the time. But PureLoneWolf is right in Jaunty is called Startup Applications.

---

### Post by nmaster on 2009-07-10
yeah, i figured it out.  this had happened to me in the past and i forgot what i did.  restarting was all i needed to do.  sorry for the bother.

---

