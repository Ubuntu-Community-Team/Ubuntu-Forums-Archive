---
title: "[HELP] Ati radeon 7000 (RV100) Update"
date: 2011-09-03
forum: General Help
---

### Post by Mini_Donut on 2011-09-03
Hi everyone! After some hours of searching on the net I've found nothing about this... 
Can anyone show me how to update my video card?

-> ATI Radeon 7000  or RV 100 

If anyone know how to do this or if have any comments about it, just post :)

Thank you!!

---

### Post by Mark Phelps on 2011-09-04
What are you using currently?

If you don't know, then do the following:
1) Open a terminal
2) Enter "lspci" (without the quote marks)
3) Look for a line containing VGA
4) Post that info back here.

BTW, there are no current Linux drivers for that card; instead, Ubuntu will install the default open-source Radeon card drivers.  This means that while you should get working 2D graphics, you will not get hardware acceleration or use of any special jacks on the card.

---

### Post by Mini_Donut on 2011-09-05
Thank you for the reply...

For the VGA line here it is: VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]


So, if there is no update for it, what can i do? :P

Thank You!

---

### Post by gandaran on 2011-09-05
> **Mini_Donut said:**
> Thank you for the reply...

For the VGA line here it is: VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]


So, if there is no update for it, what can i do? :P

Thank You!
there isn't any driver to install as ATI doesn't support these old cards, you just have to carry on using the Linux open source driver installed.

---

