---
title: "forcing grayscale on Lexmark X544 printer"
date: 2012-10-07
forum: General Help
---

### Post by Ace_NoOne on 2012-10-07
Hello,

After converting a friend to Ubuntu, their only complaint is that there's no way to make the Lexmark X544 color printer use grayscale.

We've tried both the drivers that come with Ubuntu as well as the PPD files directly from lexmark.com.

While there is an ("advanced") option "print-color-mode" in the printer options (though not in the CUPS web UI), selecting "monochrome" there and hitting "apply" resets that option to "color".

Any assistance would be greatly appreciated.

---

### Post by ezyinfo on 2013-06-17
Hi !

I have exactly the same problem with my lexmark x543 ... if somebody have the solution ...

Thanks.

---

### Post by efflandt on 2013-06-17
I have a similar C543 (just printer, not scanner) and I do not find any setting on the web interface of the printer itself or in the driver for grayscale or monochrome. But I spent some time adjusting the printer itself to get photo realistic color (instead of vivid brochure like color) and those settings work as well with a C543 we have at work. So I don't want to tamper with settings on the printer itself.

I thought maybe setting Saturation (in Advanced) to zero when printing would eliminate color, but no difference. And when I tried setting Color Correction to Manual and set the 3 colors to -5, the popup for an instant mentioned grayscale, but it still printed same color (no difference). So I am not sure what needs to be selected to "not" use printer settings.

---

