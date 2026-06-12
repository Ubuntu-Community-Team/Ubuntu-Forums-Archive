---
title: "How do I get network and volume applets back?"
date: 2010-05-14
forum: General Help
---

### Post by Mzwo on 2010-05-14
Hi,

I appear to have accidentally removed the volume and the network applets from the tray and can't find them in the "add to panel" list :oops: ... 

how do I get them back?

Thanks,
Matt

---

### Post by spiky001 on 2010-05-14
add the notifcation applet

---

### Post by Mzwo on 2010-05-14
done that.

still no network or volume.

hm.

---

### Post by Mzwo on 2010-05-15
network's back, but only - how should I put this - "half of it". its right edge has been cut off. 


volume is still awol.

what to do?

thanks,
matt

edit: network is looking its usual self again, but still no volume ...

---

### Post by Mzwo on 2010-05-16
still ...

---

### Post by dondiego2 on 2010-05-16
Can you show us a screen shot?

---

### Post by Mzwo on 2010-05-16
certainly.

as you can see - no volume. 

Matt

---

### Post by pcdave98 on 2010-05-16
Check indicator-sound is installed in Synaptic Package Manager.

---

### Post by Mzwo on 2010-05-16
it was. tried re-install, no change.

hm.

Matt

---

### Post by Directive 4 on 2010-05-16
indicator applet

also

notification area,

you need both

---

### Post by Mzwo on 2010-05-17
got both (wireless and battery work).

alas, no volume ...

Matt

---

### Post by Mzwo on 2010-05-18
bump

---

### Post by Mzwo on 2010-05-19
bump

---

### Post by mb_webguy on 2010-05-19
If you removed the indicator applet (the one with the envelope icon, where the volume icon is located as of 10.04), then you'll need to add /usr/bin/gnome-volume-control-applet to your startup applications to get the volume icon in the notification area.

---

### Post by Mzwo on 2010-05-21
you're a star, thanks!

it's back :D

Matt

PS: just one minor thing (and this is purely cosmetic): it doesn't fit with the standard theme anymore

---

