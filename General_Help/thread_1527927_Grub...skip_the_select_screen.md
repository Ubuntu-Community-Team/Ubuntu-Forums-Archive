---
title: "Grub...skip the select screen?"
date: 2010-07-09
forum: General Help
---

### Post by dtrot55 on 2010-07-09
Is there a way to just have it to where I don't need to see the GRUB screen every time I start-up or restart my computer? I almost never select any other option on the menu so in my mind it's pretty pointless to have to deal with it. 

But, if I ever had to get back to that screen, then I would have to be able to see GRUB and maybe change it back or have it to where you hit like F8 or something...just curious

---

### Post by Leppie on 2010-07-09
you can edit this in the grub defaults file, open it with an editor:
```
gksudo gedit /etc/default/grub
```then edit the following line like this:
```
GRUB_TIMEOUT=0
```save and exit, then run update-grub:
```
sudo update-grub
```this will skip the grub menu. if you want the menu to show, you have to press the SHIFT key at the time it would normally appear (e.g. after the POST screen) so it would be good to start pressing SHIFT during the POST messages.

you could also set the timer to a very low value (like 2 seconds).
```
GRUB_TIMEOUT=2
```

---

### Post by dtrot55 on 2010-07-09
Thank you!  Works great!!!

---

### Post by Leppie on 2010-07-09
you're welcome, glad it's working to your likings :)

---

