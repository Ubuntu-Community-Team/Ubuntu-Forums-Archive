---
title: "Fonts look different in xubuntu for ffox, chromium"
date: 2009-12-28
forum: General Help
---

### Post by zelhar on 2009-12-28
I noticed that when I log in into xfce session (most of the time I use kde), the fonts look different, less readable, in my browsers. 

Is there anyway to tweak this ?

---

### Post by gsmanners on 2009-12-28
The attachment shows my settings for fonts.

---

### Post by zelhar on 2009-12-28
> **gsmanners said:**
> The attachment shows my settings for fonts.

same as mine.

---

### Post by prshah on 2009-12-28
> **zelhar said:**
> the fonts look different, less readable, in my browsers. 

Is there anyway to tweak this ?

I have the same problem since 9.10; the only solution I have found is to install the NoSquint extention in firefox.

---

### Post by zelhar on 2009-12-28
I followed this link
[http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/](http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/)

> and changed /~/.fonts.conf to:
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintnone</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

I got mixed results. Some things look better, other things like for example the text I insert in this box looks blurry. 

And still there is a difference between xfce and kde font display.

---

