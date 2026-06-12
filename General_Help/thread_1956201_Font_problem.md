---
title: "Font problem"
date: 2012-04-10
forum: General Help
---

### Post by manoyth on 2012-04-10
I use Ubuntu 11.10. I have kubuntu-desktop package installed. After tweaking some settings in KDE the fonts in web browsers look ugly, both in GNOME and KDE, only in my user account. How can I restore them? (See the screenshots)

---

### Post by manoyth on 2012-04-10
In addition, firefox looks ugly.

---

### Post by kiirokurisu on 2012-04-10
KDE and Gnome can tend to conflict when it comes to font configuration, causing these kind of visual problems (and others too). For Firefox/Chrome I've found that the most reliable solution is to create a .fonts.conf file in your home directory. This will be picked up by both browsers and give you nice smooth fonts. Create the file with the following contents:

```

<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
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
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>

```

---

### Post by manoyth on 2012-04-11
There was already a .fonts.conf file. I deleted it and created another one with the contents you wrote, but nothing happened.
EDIT: I just deleted the file and the fonts are now smooth as before! Thanks!

---

