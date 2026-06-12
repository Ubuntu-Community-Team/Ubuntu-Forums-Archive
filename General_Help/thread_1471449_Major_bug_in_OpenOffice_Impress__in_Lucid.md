---
title: "Major bug in OpenOffice Impress  in Lucid"
date: 2010-05-03
forum: General Help
---

### Post by bcasanov on 2010-05-03
Hi,

I have found that when I click on "Slide Show" from the Slide Show menu in Impress on Ubuntu Lucid or enter F5, that I do not get a fullscreen slide show, and instead, get what is shown in the attached picture.  This seems to be a pretty big bug, since the problem has cropped up consistently on two computers that I have tested this on once I upgraded to Lucid.  Are there any causes of this or workarounds?

---

### Post by flipper9 on 2010-05-04
This bug was reported during the beta of Lucid, but the developers didn't see it as a big enough bug to fix.  I've resorted to using virtualbox and Office 2007 to view powerpoints.  Yeah; they didn't think it was a major bug because you can manually hide the gnome toolbars.  Yeah, right! :lolflag:
EDIT: oh wait, that's a different bug.  Oh well, it's broken several ways in Lucid.

---

### Post by atundel on 2010-05-04
Same problem here.
You can always hide Gnome's bar. :(

---

### Post by flipper9 on 2010-05-04
> **atundel said:**
> Same problem here.
You can always hide Gnome's bar. :(
Yeah, you can.  But it's a regression.  It wasn't this way before.  Besides, when you add up all kinds of "work-arounds", you end up with an operating system that's a pain to use.  Who want's that?  Ubuntu can do better.

When talking to people how great Ubuntu is (and it is), I have to add all these qualifiers: well, when you want to present powerpoints you'll have to manually hide your toolbar.  To get it to boot, you'll need to edit this file and add this string to the end of the boot parameter.  It won't work on this laptop because of X.  You'll get a video glitch here, but just ignore that. You won't be able to do surround sound, but they'll fix it eventually.  If you want to watch Hulu, you'll have to use the 32-bit flash instead of 64-bit, but it's gonna get fixed soon.  It's really better than Mac OsX and Windows.  Really!

---

### Post by andrewcd on 2010-05-11
I get a different, similar problem in 10.04.  The slideshow works, but the toolbars won't go away.  No distortion though like in that first screenshot.

Bug fixes welcome.

---

### Post by benjamimgois on 2010-05-12
> **andrewcd said:**
> I get a different, similar problem in 10.04.  The slideshow works, but the toolbars won't go away.  No distortion though like in that first screenshot.

Bug fixes welcome.

Same here, this problem happens only with my intel graphic cards. With 965 and 945 Graphics the gnome bars won't go away, on my Nvidia GF4 using nouveau it doesn't happen.

---

### Post by benjamimgois on 2010-05-12
I just realize that if you torn off COMPIZ, everything works fine. But it's definitly a regression.

---

### Post by pizza-is-good on 2010-05-12
> **andrewcd said:**
> I get a different, similar problem in 10.04.  The slideshow works, but the toolbars won't go away.  No distortion though like in that first screenshot.

Bug fixes welcome.

Exact Same problem here...
I'm disappointed.

---

### Post by xander21c on 2010-05-12
Hi guys,

I found this on launchpad 
[https://bugs.edge.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807](https://bugs.edge.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807)

looks like is a bug or regression on compiz.

If you disable compiz you get the regular behavior of the impress presentation

---

### Post by Hagar Delest on 2010-05-13
Works fine with xubuntu Lucid and Sun version of OOo: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by hugo_koopmans on 2010-09-07
de-installed compiz but still no luck, this is very disappointing.

I am a big ubuntu fan, using it for my business for years but for presentations it does not get better with OOo... also now MS is on the "open" pptx format things have turned worse... i don't want to have a VM with M$ lying around for presentations...

---

### Post by benjamimgois on 2010-09-09
> **hugo_koopmans said:**
> de-installed compiz but still no luck, this is very disappointing.

I am a big ubuntu fan, using it for my business for years but for presentations it does not get better with OOo... also now MS is on the "open" pptx format things have turned worse... i don't want to have a VM with M$ lying around for presentations...

I have the same feeling, openoffice progress is very slow, but instead use a VM i recomend you to buy the CROSSOVER software from CODEWEAVERS, it is a wonderfull solution to run microsoft office 2007 on Linux. I use it on my business and it works just fine with excelent performance and stability. Buying a license even helps the wine project, it's cheap and works great.

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

---

