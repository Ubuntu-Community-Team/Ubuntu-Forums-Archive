---
title: "laserjet 1320 printer suddenly &quot;not connected&quot; in 10.04"
date: 2010-07-04
forum: General Help
---

### Post by cloud3737 on 2010-07-04
My printer had been working in 10.04 for a couple months. It still does work when I boot from a 9.04 live CD, so I know it really is "connected" hardware-wise. Any suggestions?

---

### Post by davidmohammed on 2010-07-04
seems like a recent update has broken many hp printers.

[this guy]("http://art.ubuntuforums.org/showthread.php?t=1522632") has claimed a workaround - do they work for you?

---

### Post by cloud3737 on 2010-07-04
His "cat" method gets me a "permission denied" message. My computer doesn't have a parallel printer port so unfortunately I'm stuck using the USB cable.

---

### Post by foresthill on 2010-07-09
This worked for me on my 1320 Laser Jet on 10.4:

OK, I was able to finally get my HP Laser Jet 1320 to print. What I did was open printer properties, then go to "Device URI' and "change". At the bottom of the dialog box that opens, there is a "+" sign to the left of where it says "Connection". Click the plus sign and change the selection from "HP Linux Imaging and Printing" to "USB". That allowed the printer to work (for me anyway, YMMV).

One more thing I did to get PDF files to print was open them in Okular (you'll have to install this program, it does not come with the default install). Printing is glacially slow (probably 5 minutes for each page) but at least it works.

---

### Post by cloud3737 on 2010-07-11
That worked. Thanks very much.

---

### Post by foresthill on 2010-07-24
Well, a new kernel update as well as a CUPS update. Printing is hosed worse than ever now.

Any 1320 users come up with a workaround yet?

---

### Post by foresthill on 2010-07-26
Can't anyone figure this out? 

10.4 has been out for almost 4 months, but I can't use it because I can't print anything. What a waste. 

At least 9.10 prints good. I guess I'll just stick with that.

---

### Post by codecutter on 2010-08-02
@Foresthill.
I was having problem printing on HP Laserjet1012. It worked fine in Ubuntu 9.x, but would not work in 10.04
I installed HPLIP drivers, but could not print at all using Laserjet 1012.
Your solution (change the selection from "HP Linux Imaging and Printing" to "USB") worked fine for me.
Thanks a lot.

---

### Post by foresthill on 2010-08-07
So are you people who are able to print in 10.04 able to print PDF files? I just did a complete reinstall of 10.04 hoping to fix my printing problems. I reinstalled all 300 mb's of updates too. 

As of now, I can print regular word processing files. But if I try to print a PDF, the green light on the printer just blinks and blinks, and after about 10 minutes the yellow light also starts blinking and nothing ever prints.

Almost everything I print is in PDF format, so I am currently hosed and can't use 10.04 at all for everyday work use.

So can anyone print PDF files or is it just me?

---

