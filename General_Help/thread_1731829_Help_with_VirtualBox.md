---
title: "Help with VirtualBox"
date: 2011-04-17
forum: General Help
---

### Post by IHeequ5i on 2011-04-17
I have an ATI Radeon card in my desktop PC that runs Maverick. I've installed VirtualBox and set up a virtual PC that runs Windows XPSP3. But it insists on using the generic VGA adapter for graphics.

I've tried downloading the latest catalyst package from ATI (AMD it is now), and while the Catalyst control center installs, the actual video drivers will not. It is apparently not detecting the video card properly.

Any help greatly appreciated. If I can get this working, it's one step closer to becoming Windows-free.

---

### Post by coldraven on 2011-04-17
I'm not sure that what you're trying will work.
VirtualBox is presenting virtual hardware to the guest OS, hence the name!
Someone else might have a better idea of how this works.

---

### Post by uidb4056 on 2011-04-17
You Have to install the Guest Additions on XP, see the help of VirtualBox

---

### Post by howefield on 2011-04-17
You are restricted to the virtual drivers supplied by VirtualBox, as said above, installing guest additions will give you as good as it gets.

---

