---
title: "Firefox 3.5 font problem"
date: 2009-10-30
forum: General Help
---

### Post by Finalfantasykid on 2009-10-30
I am probably missing something stupid, but the fonts in firefox don't seem to be rendering consitently with the rest of the OS.  If you look at the screenshot below, compare the font in the menubar to the top panel text of Ubuntu.  I'm pretty sure the font is the same, but in Firefox it doesn't seem to be doing the Full Hinting that I have it set to.

[http://img40.imageshack.us/img40/1742/screenshotfc.png](http://img40.imageshack.us/img40/1742/screenshotfc.png)

---

### Post by Finalfantasykid on 2009-11-01
*Bump*

---

### Post by kerry_s on 2009-11-01
you need to use the old "~/.fonts.config" fix.

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <edit mode="assign" name="rgba">
  <const>rgb</const>
 </edit>
</match>
<match target="font">
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
</match>
<match target="font">
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
</match>
<match target="font">
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
</match>
</fontconfig>

```

---

### Post by Finalfantasykid on 2009-11-01
Thanks that fixed the problem.  Except it had to be ~/.fonts.**conf**

---

### Post by kerry_s on 2009-11-02
> **Finalfantasykid said:**
> Thanks that fixed the problem.  Except it had to be ~/.fonts.**conf**

my bag, i'll try & be more careful next time. i was in the process of switching back to debian lenny, so my mind was there. :p

---

