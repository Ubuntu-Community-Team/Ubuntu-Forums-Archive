---
title: "Installed New Grahpics Card, PC no longer functions"
date: 2011-03-15
forum: General Help
---

### Post by marenum on 2011-03-15
I think I may have finally killed my computer. My graphics card broke down a month ago, it was an XFX Nvidia 8600 GT. I swapped it out with an old 7600 GS, and it worked fine. XFX sent me an HD 4650 as a replacement, which I installed today. I powered my PC back on and it seemed to run fine but I had no picture, and the mouse didn't light up like it normally does. I put the 7600 GS back in and tried again. Nothing. I'm worried that the motherboard is malfunctioning or something. Does anyone have a clue what happened here?

---

### Post by 3Miro on 2011-03-15
Going from Nvidia to ATI, you should uninstall all Nvidia drivers first, then put the new card and it should work (I have done that on 10.04).

However, your problem seems more convoluted. You say that not even the mouse appears, if you cannot post (i.e. see some picture or enter the BIOS), then you have a hardware issue. 

- Try clearing the CMOS too, some setting may be causing an ATI-NVIDIA conflict.

- Try taking the card out and then putting it back in, perhaps it didn't fit in the socket properly. 

I have no other ideas.

---

### Post by LetsMugSanta on 2011-03-15
Just in case, because electronics are always stupid. Try reseating the RAM as well.

---

### Post by marenum on 2011-03-15
Thank you for your replies. I took out 2 512mb ram sticks and it booted up with the 7600 GS. I'm a bit nervous to put the ati card back though.

---

### Post by 3Miro on 2011-03-16
> **marenum said:**
> Thank you for your replies. I took out 2 512mb ram sticks and it booted up with the 7600 GS. I'm a bit nervous to put the ati card back though.

Try putting the RAM back in and then see if you can pass memtest (I think you have to download the Ubuntu alternate install CD). If memtest fails, then you know the problem is with the RAM. If memtest passes then:

- Uninstall the Nvidia driver from Ubuntu
- Remove the Nvidia card from the slot
- CLEAR THE CMOS (this is the crucial step)
- Put the ATI card in and boot

---

