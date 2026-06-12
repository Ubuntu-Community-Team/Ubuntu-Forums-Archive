---
title: "TiLP2 (TI-84 Plus)"
date: 2010-12-14
forum: General Help
---

### Post by Ginfuru on 2010-12-14
Hello, I've found a little program called TiLP2 to put applications on my TI-84 Plus.

I've connected my TI-84 Plus to my PC and opened the program.
I've inserted a attachment on how the program looks like (it's a screenshot).
But the program won't link with my calculator.
In other words, the program doesn't detect my calculator.

I'd appreciate it if someone could help me with this.

Kind Regards. 

PS: I'm fairly new to Ubuntu and new to the forums, so be easy on me. :p :lolflag:

---

### Post by Habeouscorpus on 2010-12-15
Are you sure that it works with your computer? Are you using the factory cord? (They can be picky.) Have you tried mounting it with disk utility or terminal? Have you tried turning on the calculator, then connecting? 

(Sorry for the questions, but we must know.)

---

### Post by mrhhug on 2011-09-04
i use tilp all the time. I use the cable came that came with my cell phone, it didn't seem to matter. So plug in your ti and then run ```
lsub
```ubuntu should show your ti as an addressable usb device - if this doesn't work nothing else will work. Installed from repos ```
sudo aptitude install tilp
```the first thing i had to do was run it as root ```
gksduo tilp
```because it gave me a permisions error about the usb - probobly could have chmoded the device but ehh. it still didn't detect by itself. i had to right click on the left pane where yours says "none -> null" and then change device. tick the scan at startup. restart tilp and everything went alright for me. just drag and drop from then.


ohh if i transferd too many items at a time it would die - this may be the cable but i only transfer stuff every few months so it wasn't that serious

---

### Post by mrhhug on 2011-09-04
one more note, the ti has to be on for the usb to work.

---

