---
title: "Radeon 9200SE Driver Question. &quot;fglrx&quot; or &quot;radeon&quot;? Which is Faster?"
date: 2006-03-31
forum: General Help
---

### Post by Bandit on 2006-03-31
Hello Everyone,
I purchased a Radeon 9200SE 128MB about 2 months ago. 
I have been switching it in and out with my nVidia FX5500.
The Radeon runs smoothly and stable.
The nVidia runs fast, but crashes Xorg left and right.
I have the radeon installed now, works well. But it only gets 723 FPS in GLXgears.
My question is if I use the ATI proprietory drivers "fglrx" will they speed up my video card?
I am currently using the Xorg7 "radeon" driver.
Thanks,
Joey

---

### Post by blitzer on 2006-04-24
I have a Radeon 8500DV using the "fglrx" and what I have found is that if you got it working then you are way ahead of the rest :p  The "fglrx" turns on 3d acceleration and gives you full usage of 3d Vid card. 

Try it in different games like "Americas Army" and switch drivers to test.  Post your results for the rest of us....

---

### Post by barbarian on 2006-08-11
For me - radeon, i have 2000fps. And with fglrx maximum i ever had - ~1400 fps.

btw try:
*Option "EnablePageFlip" "True"*

in your xorg.conf

---

