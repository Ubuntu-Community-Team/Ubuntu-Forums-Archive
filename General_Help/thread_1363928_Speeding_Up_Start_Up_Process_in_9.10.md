---
title: "Speeding Up Start Up Process in 9.10"
date: 2009-12-25
forum: General Help
---

### Post by lightzout on 2009-12-25
Hi, 
i am relatively new to the whole linux world. I realized that after the last updates i have installed the start up performance of my system shrunk.
I use both Linux and Windows 7 on my laptop. After i have selected to start Ubuntu via GRUB it takes est. 35 seconds to boot into the GDM and another 15 seconds from GDM to my Desktop after entering my PW and pressing ENTER.
I have tried to disable unnecessary services at start up, but i can't see no effect.

Any suggestions would be greatly appreciated.

regards Pascal

---

### Post by unmole on 2009-12-25
This might help you [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by lightzout on 2009-12-25
I have already taken  a look at this but there is no improvement i can "feel". I have found another guide here on the forums using readahead ([http://ubuntuforums.org/showthread.php?t=565651]("http://ubuntuforums.org/showthread.php?t=565651")). 
But until now i can't get it to work until now, because my readahead-watch command is missing. -.-

---

### Post by warfacegod on 2009-12-25
Are you using Compiz? The enhanced graffix tend to take almost twice as long to boot on my computer when they are on. If this is the case for you, you might try installing Compiz-Switch, it's a very easy way to turn compiz graffix on and off. Just turn them off before shutting down and turn them back on after you've finished booting up. For me, it takes about 3 seconds, on or off. much faster than doing it through the Visual Effects tab in Appearance Preferences. Hope this helps.

---

