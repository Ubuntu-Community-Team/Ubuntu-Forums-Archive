---
title: "unclear fonts after installing systemsettings-kde4"
date: 2010-12-08
forum: General Help
---

### Post by kayvee on 2010-12-08
I use a few KDE programs on my Ubuntu install. In order to be able to change a few settings, I recently installed systemsettings-kde4 and tweaked a few things - color schemes, icon theme, font sizes, etc. Ever since I did that, the font anti-aliasing settings in firefox are lost. Peculiarly, only the fonts that are part of the website are not clear. The menu fonts (even in Firefox), fonts that I type into forms in a website, etc are still clean. You see it to a small extent in the attached screenshot. It is more discernible to me though. 

How do I fix it? Please help.

---

### Post by ram0s on 2010-12-12
I have exactly the same problem, and it is extremelly frustrating. But for me, it is ALL of the text in firefox, be it actual webpages or the browser menus, bookrmarks, etc.

Also, the same happens in Google Chrome, but only on webcontent. The text on menus looks fine. On Firefox, it's everywhere.

---

### Post by ram0s on 2010-12-12
Hey I fixed it. 

Went to /home/[user_name]/.fonts.conf and configured it according my gtk settings.

These are my settings: 

```
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
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

See if these work for you, or change them to your liking.

Cheers.

---

### Post by kayvee on 2010-12-13
Thank you ram0s. It worked for me too!

---

### Post by IgnatiusReilly on 2011-06-09
I had the same problem and it worked for me too :p

Thanks a lot

---

