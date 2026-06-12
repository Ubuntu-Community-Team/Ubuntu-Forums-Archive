---
title: "onboard graphics with aspeed ast2050 ???"
date: 2010-03-03
forum: General Help
---

### Post by tony.morse on 2010-03-03
Hi, I've just built a tesla machine using the tyan s7025 motherboard. I've installed ubuntu 9.04 but I can only get 800x600 resolution from the onboard graphics but it should support 1600 x 1200 (which is an ASPEED AST2050 chipset). Does anyong have any ideas how to get this onboard graphics working properly in ubuntu??
I've updated the drivers to the latest ones which apparently support redhat and susi but there is no mention of ubuntu.

Cheers

---

### Post by tony.morse on 2010-03-03
Ok, for anyone else with the same problem here is the solution...

1. install a 32-bit version of windows
2. get the drivers from the aspeed website
3. run the VBIOS flash utility to upgrade the VBIOS on the chipset (only works in windows 32-bit)
4. remove windows forevermore (hopefully)
5. re-install ubuntu

Job done, you can also update the driver in ubuntu but it didn't seem necessary for me

---

### Post by havexz on 2010-12-11
any idea on which file to choose for Ast2050 8MB.

This is the snipped from the Readme. 
4.VBIOS Image Descriptions for AST1100/2050:
- D21Gx16.200:  DDR2 1Gb(64Mx16) 1pcs 200MHz
- D2512x16.200: DDR2 512Mb(32Mx16) 1pcs 200MHz
- D1512x16.200: DDR  512Mb(32Mx16) 1pcs 200MHz

Also to update, the usage is 

flash [updated image file] [old image file]

what is the [old image file]?

I have this KCMA-D8 motherboard and its really painful to set it up.

---

