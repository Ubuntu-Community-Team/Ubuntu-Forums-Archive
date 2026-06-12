---
title: "Ubuntu 9.10, Best but Brasero is worst"
date: 2009-11-02
forum: General Help
---

### Post by BharatBSahni on 2009-11-02
I downloaded Ubuntu 9.10, it is jazzy, speedier, beautiful, but the CD ISO Image Burner Brasero is worst.

It does not write the CD ISO Image on 1x or 2x i.e. low speeds,
thus the CD ISO Images written by Brasero are poor, does not work properly.

It spoils the CDs, does not blanks the CDs, properly and hangs.

Is there any other Good CD ISO Image writer for Ubuntu 9.10,

Please guide how to uninstall Brasero and install the Good CD ISO Image writer on Ubuntu 9.10

Bharat

---

### Post by HiImTye on 2009-11-02
first thing, disable the normalize plugin in brasero. you will likely see a noticable difference.

otherwise, check synaptic (administration>Synaptic Package Manager)

---

### Post by donato roque on 2009-11-02
I seldom do burning.  But it seems to me the best way to burn ISO is to right click on it and choose 'Write to Disc' in the options.

---

### Post by BharatBSahni on 2009-11-04
> **donato roque said:**
> I seldom do burning.  But it seems to me the best way to burn ISO is to right click on it and choose 'Write to Disc' in the options.

Yes I have tried all the above, in Ubuntu 8.04, right click gives the write option in the drop down Menu, clicking which shows the option to select speed from 1x to numerous desirable Speeds.

Using 2x and around I burnt Ubuntu 9.10 iso successfully.

But after installing Ubuntu 9.10, I am unable to burn more CDs from the downloaded ISO Image of 9.10, as right clicking on ISO image, the write to disk does not show the different speed options, it shows only Maximum Speed or 50x Speed approximately.

I have spoiled number of CDs, on which the ISO image file is being regularly unsuccessfully burnt hence I can not boot and install again.

Help

---

### Post by jmszr on 2009-11-04
BharatBSahni,

I would recommend that you try k3b as a CD burner:

```
sudo apt-get install k3b
```

or perhaps it's available in the Software Center.

I've never had a problem with k3b

---

### Post by BharatBSahni on 2009-11-05
Thanks jmszr,

I shall give it a try, but is it not a Kubuntu Utility ?
Further, are you sure it does give the option, to burn at lower speeds, on an Ordinary Recordable CD ?

'cause I have found out that a ISO File burnt does not run easily till it is burnt at low speed, that is what Ubuntu BurningISO Howto on the Ubuntu site recommends.

---

### Post by Jakiejake on 2010-06-17
> **BharatBSahni said:**
> I downloaded Ubuntu 9.10, it is jazzy, speedier, beautiful, but the CD ISO Image Burner Brasero is worst.

It does not write the CD ISO Image on 1x or 2x i.e. low speeds,
thus the CD ISO Images written by Brasero are poor, does not work properly.

It spoils the CDs, does not blanks the CDs, properly and hangs.

Is there any other Good CD ISO Image writer for Ubuntu 9.10,

Please guide how to uninstall Brasero and install the Good CD ISO Image writer on Ubuntu 9.10

Bharat

How Long Does it take to copy at 1X!

---

### Post by Jakiejake on 2010-06-25
FYI Gnome Baker has a 1X Setting!

---

