---
title: "Firefox title fonts"
date: 2009-09-16
forum: General Help
---

### Post by toontastic on 2009-09-16
I'm having problems with the fonts in firefox where I can't explain it as well as I can show it so I've attached a screenshot. Basically if you look at the titles and the menus the font looks awful. It all started when my system performed an upgrade in version 3 of firefox. I've since upgraded through version 3.52 and 3.5.3 using ubuntuzilla and I'm still having the same problems. I hope someone can help cause it looks awful.

Thanks.

---

### Post by winotree on 2009-09-16
That looks like Lucinda font.  What is your font setting in Edit | Preferences | Fonts and Colors | Advanced ??  Although I know you've already checked...

---

### Post by lovinglinux on 2009-09-16
Create a file in your home directory, naming it **.fonts.conf**, if it does not exists, then add the following (or replace previous content):

```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

This should probably fix the font issue.

---

### Post by nanotube on 2009-09-16
if the suggestion above doesn't work, there are a few other alternatives posted on this thread:
[http://ubuntuforums.org/showthread.php?t=1200992](http://ubuntuforums.org/showthread.php?t=1200992)

p.s. hey lovinglinux, how goes it ? :)

---

### Post by lovinglinux on 2009-09-16
> **nanotube said:**
> if the suggestion above doesn't work, there are a few other alternatives posted on this thread:
[http://ubuntuforums.org/showthread.php?t=1200992](http://ubuntuforums.org/showthread.php?t=1200992)

p.s. hey lovinglinux, how goes it ? :)

I'm fine. You?

The only thing is that I was struck with programming laziness this week :) I guess is because I'm porting an extension to Windows. I feel completely lost when booting into Windows now. I keep trying to use compiz window picker and launching the terminal to install applications :)

---

### Post by nanotube on 2009-09-16
> **lovinglinux said:**
> I'm fine. You?

still alive, which is pretty good in itself. :)

> 
The only thing is that I was struck with programming laziness this week :) I guess is because I'm porting an extension to Windows. I feel completely lost when booting into Windows now. I keep trying to use compiz window picker and launching the terminal to install applications :)
heh, i know what you mean, both about being struck by laziness (writing a dissertation here), and feeling out of place on windows. :)

---

### Post by toontastic on 2009-09-17
> **winotree said:**
> That looks like Lucinda font.  What is your font setting in Edit | Preferences | Fonts and Colors | Advanced ??  Although I know you've already checked...

Your right I had and the fonts are set to Serif so not that.

---

### Post by toontastic on 2009-09-17
> **lovinglinux said:**
> Create a file in your home directory, naming it **.fonts.conf**, if it does not exists, then add the following (or replace previous content):

```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

This should probably fix the font issue.

YES!!!! thank you thank you thank you :guitar: :KS

---

### Post by lovinglinux on 2009-09-17
> **toontastic said:**
> YES!!!! thank you thank you thank you :guitar: :KS

You are welcome, welcome, welcome :)

---

### Post by simartem on 2009-09-21
**thank you.**

---

### Post by Vaphell on 2009-09-21
home directory = your main directory (Places->Home from menu), it's got home icon and it keeps all your files and settings.
its absolute path is /home/yourname - /home keeps home dirs of all users.

---

