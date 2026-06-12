---
title: "Drawing Tablets for 11.10"
date: 2012-02-09
forum: General Help
---

### Post by gr8 on 2012-02-09
Are there any drawing tablets that are confirmed to work in 11.10?

I'm reading older posts on here and it seems a lot of the older tablets no longer work in 11.10 due to the lack of the xorg.conf file.

I'd prefer to use a non Wacom (maybe VT Pen or Genius MousePen) because the Wacom is expensive.

---

### Post by MrBandicootKid on 2012-02-09
You mean like, drawing programs?
 
If thats what you mean, Kolourpaint is a great one.

---

### Post by WinfriedG on 2012-02-09
I don't know, if tablets are confirmed here; however I use a WACOM tablet - rather old but very useful its pressure sensitive: CTF-420G - in conjunction with mypaint and it works very well. I have Lubuntu 11.10 installed

---

### Post by gr8 on 2012-02-09
I was referring to the tablet hardware. There are different tablets by manufacturers such as Wacom. They're not like iPad tablets, they are tablets only for drawing. I need one for 11.10. Thanks for the software suggestion.

---

### Post by Favux on 2012-02-09
Hi gr8,

They all pretty much work unless they are very new.

The Wacom, Waltop (most of them), and Hanwong work on the Wacom X driver.  The Aiptek tablets work on the Aiptek X driver.  And the tablets (Genius Pen etc.) that worked on the WizardPen driver now work on the evdev X driver.

Nikolai Kondrashov's DIGImend site:  [http://digimend.sourceforge.net/](http://digimend.sourceforge.net/)  has a table of supported "WizardPen" models:  [http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v0.4](http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v0.4)

Nick just got several tablets that weren't working, the KYE Systems EasyPen i405X, EasyPen M605X, and MousePen i608X, working.  He figured out the "secret handshake" they were using to initialize themselves.  He's working on the kernel patches which he should be submitting to the kernel in the next few days.  He'll likely also backport support for Oneiric's 3.0 kernel by updating his kernel patches.  So for those models you'd need to compile a module or two in the kernel's hid directory until probably Ubuntu 12.10.

---

