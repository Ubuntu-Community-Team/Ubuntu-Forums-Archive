---
title: "Flash awkwardness in 10.04"
date: 2010-05-03
forum: General Help
---

### Post by Sandertje on 2010-05-03
Hi!

I'm having a problem with flash on ubuntu 10.04 (64 bit) Flash animations will show, but when trying to click elements (hovering over them seems to function normally), nothing happens. For instance, in youtube, when I click the play button, it does not pause (or play again when paused), neither can I change the volume. The problem usually occurs when having *two* flash sites open at the same time (e.g. two youtube vids, or just two random sites that use flash). Any idea as how to fix this?

---

### Post by Taus on 2010-05-03
Hi Sandertje,

i had the same problem... i noticed that i could work it around by holding down the right mousebutton on the flash object and then left click the flash button i wanted to click while still holding down the right mouse button.

i then found out i could completely fix it by doing this from the terminal:

sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this before the last line of text “export GDK_NATIVE_WINDOWS=1&#8243;, then save and restart the application that uses flash.

it worked for me :) but i think it's only for 64 bit version of ubuntu. I hope it works for you as well..

cheers

---

### Post by Cynical on 2010-05-03
If you haven't already you may want to update to the latest 64-bit beta of flash. You can find it [here](http://labs.adobe.com/downloads/flashplayer10_64bit.html).

To install it simply extract the archive, navigate to that directory in a terminal, and then type ```
sudo mv libflashplayer.so /usr/lib/firefox-3.6.3/plugins
```

---

### Post by Sandertje on 2010-05-03
The rightclick thingy does seem to work for me as well! :D

I'm gonna try editing the npviewer xD!

Thanks so much!

---

### Post by Sandertje on 2010-05-03
I'm having open three flash sites and all works perfectly now! :D
Thanks again!

---

### Post by Taus on 2010-05-03
No problem :)

i'm glad it worked for you as well..

---

### Post by the-rosbif on 2010-05-03
I had the same issue before and this fixed it:


    * Hit ALT+F2 and enter
    * gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
    * add the following line BEFORE the last line of text
    * export GDK_NATIVE_WINDOWS=1
    * Save.
    * Restart any applications using flash

---

### Post by Vaphell on 2010-05-03
seriously consider using native 64bit flash instead of wrapping it up with ndiswrapper. Latest 64bit beta versions available at adobe.com appear to be rock solid.

---

### Post by alion1234 on 2010-05-03
Awesome, Problem solved, cheers

---

