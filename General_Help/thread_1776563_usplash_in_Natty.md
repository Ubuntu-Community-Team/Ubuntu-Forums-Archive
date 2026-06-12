---
title: "usplash in Natty"
date: 2011-06-06
forum: General Help
---

### Post by cacs on 2011-06-06
Hi.
I would like to put a usplash in Natty. I was googling around and only found "how to"'s for earlier versions of Ubuntu.

Already changed my backbround login picture and logo using "ubuntu tweek", and the grub splash. After some messy, all i got is a bunch of msgs and no usplash! :(

Is that possible?

Thank you.

---

### Post by raja.genupula on 2011-06-06
check the file 
/etc/grub.d/05_debian_theme 

there reflect your path of desired wallpaper at the WALLPAPER

hopes it will work for you

---

### Post by FormatSeize on 2011-06-06
I'm not sure the very specific name for it, but they have changed something about the way the booting program works to allow for much faster (supposedly under 10 seconds) boot time. As such, you can no longer have the usplash, such as you could in 9.04 or some other older versions. 
 
I  learned about a month ago that 9.04 is "no longer" "supported", so I moved up to 10.04, and to my dismay, I learned that I couldn't have the usplash from 9.04.

---

### Post by cacs on 2011-06-06
> **raja.genupula said:**
> check the file 
/etc/grub.d/05_debian_theme 

there reflect your path of desired wallpaper at the WALLPAPER

hopes it will work for you

Hi.
It was by looking to that file that I was able to change grub background... but not the usplash!
Thank you.

---

### Post by cacs on 2011-06-06
> **FormatSeize said:**
> I'm not sure the very specific name for it, but they have changed something about the way the booting program works to allow for much faster (supposedly under 10 seconds) boot time. As such, you can no longer have the usplash, such as you could in 9.04 or some other older versions. 
 
I  learned about a month ago that 9.04 is "no longer" "supported", so I moved up to 10.04, and to my dismay, I learned that I couldn't have the usplash from 9.04.

Hi.
I think that is a step back, although it must work since a new installation has the default ubuntu usplash!
Since many people look for this info the people from ubuntu would let us to do it with a simple way!
Thank you!

---

