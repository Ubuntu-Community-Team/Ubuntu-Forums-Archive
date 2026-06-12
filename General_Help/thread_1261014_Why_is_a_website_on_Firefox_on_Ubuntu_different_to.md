---
title: "Why is a website on Firefox on Ubuntu different to my Firefox in Windows?"
date: 2009-09-08
forum: General Help
---

### Post by infocom on 2009-09-08
May not be the right place, perhaps Mozilla should be asked I don't know, but webpages I have developed to work with Firefox using my XP machine look different to that on Ubuntu Firefox. 

I was going to start using my Ubuntu for web development, but I cant if when viewed in Firefox on Windows it looks different. I know IE has this issue but you can add code on your site to call a different stylesheet if its IE, but dont know how to do it for different operating systems. 

Ubuntu Firefox is version 3.0.13 but XP Firefox is 3.5.2, but never seen any differences before when upgrading to a newer version on Firefox on my XP. i.e. there were no changes from v 3.0.13 to 3.5.2 on my XP. 

Thanks

---

### Post by credobyte on 2009-09-08
First and foremost, fonts and controls ( custom text box style, etc. ). Actually, if it looks good in Ubuntu, it looks even better in Windows ( that's just from what I've noticed lately ).

---

### Post by Rob_H on 2009-09-08
> **infocom said:**
> May not be the right place, perhaps Mozilla should be asked I don't know, but webpages I have developed to work with Firefox using my XP machine look different to that on Ubuntu Firefox.

Can you be more specific? I am a web developer as well and I don't notice a difference, other than fonts and the native look of some controls, but that's to be expected among various platforms. You'll see similar differences if you use a Mac.

---

### Post by Bear Knuckle on 2009-09-08
Please be more specific on the differences, since some rendering are effected by settings in the operating system - like fonts and stuff. So if there are differences in the settings of the os, there will be differences in the rendered webpages.

---

### Post by infocom on 2009-09-08
Actually its not as bad as I originally thought, but still out...

The two main differences I can see on a webpage so far are:-

1) Absolute/Relative positioned elements are slighlty out. So I want to align something up perfectly using potisitioning I cant. In Firefox XP its about 10 pixels down and 5 pixels to the right compared to Firefox Ubuntu. Luckily for this particular element I dont need perfect alignment.

2) Form fields are much wider in Ubuntu Firefox. I have a size 22 for a text box in a left column and on XP its perfect within a 160 pixel wide box with a suitable margin either side. In Ubuntu Firefox it expands quite a lot over the edge of the container and into the main content. Ubuntu Firefox does have a border with padding around the form fields compared to XP but thats not large enough to cause this extra width. I had to specify a fixed with of the text box in the stylesheet. but the form still looks different a little. 

For the font I am using Helvetica because I know this is supported in Ubuntu and XP so they will be the same rather than some Windows font not supported on Linux.

---

