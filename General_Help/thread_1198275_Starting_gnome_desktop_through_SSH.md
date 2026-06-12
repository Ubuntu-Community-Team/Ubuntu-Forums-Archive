---
title: "Starting gnome desktop through SSH"
date: 2009-06-27
forum: General Help
---

### Post by MarcG on 2009-06-27
I posted this question some time ago, but now have problems. The remote machine, a Shuttle gaming PC connected to a TV, sat unused for a long time and both it and my laptop have been upgraded to Hardy.

I want to ssh -X into the remote from my laptop and then run some desktop on it so I can get to the different configurations on the Shuttle. I can ssh -X into it fine and run things like Firefox. But if I try to start gdm, nothing happens. A ps shows gdm is running, but no screen shows up. So how do I get that going?

Question 2: And once that works, how do I redirect the X output so that the video shows up on the TV instead of the laptop. I want to use my laptop's keyboard, mouse, etc., but have it show up on the TV. That will probably be the normal operating mode once things get going. For now I just want to run Hulu on there.

---

### Post by nandemonai on 2009-06-27
> **MarcG said:**
> I posted this question some time ago, but now have problems. The remote machine, a Shuttle gaming PC connected to a TV, sat unused for a long time and both it and my laptop have been upgraded to Hardy.

I want to ssh -X into the remote from my laptop and then run some desktop on it so I can get to the different configurations on the Shuttle. I can ssh -X into it fine and run things like Firefox. But if I try to start gdm, nothing happens. A ps shows gdm is running, but no screen shows up. So how do I get that going?

Question 2: And once that works, how do I redirect the X output so that the video shows up on the TV instead of the laptop. I want to use my laptop's keyboard, mouse, etc., but have it show up on the TV. That will probably be the normal operating mode once things get going. For now I just want to run Hulu on there.

GDM will default to a local X session. Not sure how to pipe it out via ssh -X.

From the sounds of things something like VNC may be more useful to you.

I'm sure there are ways and means though. Perhaps using the DISPLAY ENV variable. It's been ages since I've done this myself so I'll leave it to someone with more experience. ;)

---

