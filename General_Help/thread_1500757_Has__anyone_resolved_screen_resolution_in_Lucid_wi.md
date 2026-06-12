---
title: "Has  anyone resolved screen resolution in Lucid with intel815 chipset??"
date: 2010-06-03
forum: General Help
---

### Post by rajn on 2010-06-03
I cannot get the normal 1024x768 resolution on Vaio. I have the 10.4 Lucid installed (it was a fresh install). The default res is 640x480.
So far I am managing by creating an xorg.conf file, editing an old version which ran on Karmic 9.10. However, xorg.conf generates other problems such as Cap and Scroll lock blinking and system hanging while logging out.
It got resolved if xorg.conf is removed but screen resolution is not the best.

Is there a solution to this screen resolution issue for Lucid which does not use xorg.conf? I looked and searched a lot but cannot find any pointers.

---

### Post by rajn on 2010-06-04
Bump ! 
Anyone?

---

### Post by dcstar on 2010-06-05
> **rajn said:**
> I cannot get the normal 1024x768 resolution on Vaio. I have the 10.4 Lucid installed (it was a fresh install). The default res is 640x480.
So far I am managing by creating an xorg.conf file, editing an old version which ran on Karmic 9.10. However, xorg.conf generates other problems such as Cap and Scroll lock blinking and system hanging while logging out.
It got resolved if xorg.conf is removed but screen resolution is not the best.

Is there a solution to this screen resolution issue for Lucid which does not use xorg.conf? I looked and searched a lot but cannot find any pointers.

Lucid **can** use xorg.conf, it does not need it usually because the autodetect works for most setups.

Search for other posts with your video chipset.

---

### Post by Spr0k3t on 2010-06-05
I have a system with the 815 chipset and used this post to fix the screen resolution: [http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

Hope that helps.

---

### Post by Spr0k3t on 2010-06-05
> **rajn said:**
> ...xorg.conf generates other problems such as Cap and Scroll lock blinking and system hanging while logging out.

That is a segfault btw.  Not sure how to pull up the information on what caused it, but I do know for a fact the blinking of those two is related to a segfault.

---

