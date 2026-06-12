---
title: "How To Get Flash To Work With 64 Bit - The EASY Way"
date: 2009-11-22
forum: General Help
---

### Post by Ghostpup on 2009-11-22
I tried Firefox, Opera, and Empathy and had the same troubles. It's more luck than sense, but I just downloaded Seamonkey through Ubuntu Software Center and everything Flash works perfectly.

---

### Post by Mr Nemo on 2009-11-22
I had a lot of problems with my flash player when I first started using Ubuntu, which wasn't to long ago. The easiest way to install flash player is to either install it using synaptic or download the latest flash file for 64 bit from the link below and move it to the proper file which should be /usr/lib64/mozilla/plugins. The file should be libflashplayer.so. Thats all I had to do and my flash works pretty damn good. Of course I think you will run into a few problems on a few sites no matter what but I haven' t had any problems so far and the buttons work. If that doesnt work make sure the flash plugin is in the other lib files under mozilla plugins.

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

---

### Post by nimrodwebdesign on 2009-12-08
Fantastic this worked for me!

What I don't understand is how it worked on some sites and not others, it looked like it was down to the way the flash it was embedded in the page. With _just_ an embed tag it worked (like on the adobe flash test page), with with the seemingly standard object _and_ embed tags it didn't work. I don't understand that. Is it an Opera bug?

Well anyway, thanks for the solution :D

---

