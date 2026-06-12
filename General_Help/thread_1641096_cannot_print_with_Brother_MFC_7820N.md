---
title: "cannot print with Brother MFC 7820N"
date: 2010-12-08
forum: General Help
---

### Post by emerick7 on 2010-12-08
I can no longer print to my wireless Brother MFC 7820N. I've tried all the google search solutions and have tried all the variants of the files in cups.

Is anyone have this working in 10.10? How should I configure it? Thanks!

Also, this printer is working well for an xp machine on the same network.

---

### Post by emerick7 on 2010-12-09
has anybody used this printer before?

---

### Post by Floydius on 2010-12-14
I was just able to get a test page to print properly using the instructions and the drivers from the Brother linux page here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Prior to using these drivers and instructions, I was unable to get the MFC 7820n to work on 10.10.  (I'd never tried it on a previous version.)

In short, I downloaded both the LPR and the cupswrapper driver from here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7820N](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7820N)

then followed the step-by-step instructions here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Good luck!

---

### Post by emerick7 on 2010-12-24
thanks for the reply.

I actually got it working much easier. plugging in the IP address for it in the "find new printer" thing brought it up in an instant. not sure what it used before but it definitely wasn't that. now it's never been more reliable.

---

