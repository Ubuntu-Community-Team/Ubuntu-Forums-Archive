---
title: "Update font rendering in applications like firefox?"
date: 2009-11-01
forum: General Help
---

### Post by boom2k1 on 2009-11-01
From the Appearance Preferences->Fonts, I selected "Best shape" as the option for font rendering. 
It immediately felt so much better to my eyes in some of the text on the desktop: ie. Applications, Place, System, fonts in the Windows List.

However, I believe some applications like firefox was still rendered by Subpixel smoothing. For example, I should at least believe that the menu bar to be rendered by "Best shape".
Another application is Skype... but I remember this is a QT3/4 related thing?

How do I update those applications?

Thanks!

---

### Post by boom2k1 on 2009-11-01
I am still looking for a reply, but I have solved my own problem by using a "hack".

From a forum post, I learned that some people put a file called .fonts.conf in the /home/USER_NAME directory. I probably had done it in earlier installations (8.04->9.04), and that was why the firefox menu used to look so much better.

Anyway, my .fonts.conf looks like this:

```

<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
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
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

After putting this file inside my home directory, I restarted firefox and immediately noticed the difference.
How pretty the fonts look now!


- I probably did not really update the font rendering in firefox and probably had just changed something else to make it work.

Here is an article I googled:
[http://tombuntu.com/index.php/2008/10/15/tweak-your-font-rendering-for-better-appearance/](http://tombuntu.com/index.php/2008/10/15/tweak-your-font-rendering-for-better-appearance/)


I wish applications like firefox would obey the central font rendering rule and a hack like this one is really are annoying for users.


- an alternative might be to use a software called fontmatrix (Ubuntu Software center). I noticed that when I installed this file, it created a .fonts.conf inside the home directory and such file had a link to its configuration folder, so I assume changes made in the program would be reflected in system wide applications as well. I hadn't figured how that sophisticated program works yet.

---

