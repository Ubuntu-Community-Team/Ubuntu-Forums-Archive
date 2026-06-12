---
title: "USB modem doesn't make sound"
date: 2009-08-24
forum: General Help
---

### Post by yvr214 on 2009-08-24
Hi,
 

 I bought a USB modem, USRobotics Model 5637 which I want to use as fax with Efax-gtk. The modem seems to dial with Efax-gtk but doesn't make a sound. Is that normal with USB modems?  
 If I do lsmod I do see the cdc_acm kernel module as I should for this modem. I there any other module needed here? Sound seems to be O.K on this Ubuntu.
 

 What can be the problem?
 

 Thanks for any help.

---

### Post by dandnsmith on 2009-08-24
I wouldn't worry as long as it works - the pic suggests that there is only the one connection to the computer, whereas PCI card modems often have a connection to your sound card to make the sounds. I suspect that there is no sound-making device builtin.

---

