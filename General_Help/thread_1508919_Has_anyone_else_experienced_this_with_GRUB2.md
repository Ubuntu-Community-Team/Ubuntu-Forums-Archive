---
title: "Has anyone else experienced this with GRUB2?"
date: 2010-06-13
forum: General Help
---

### Post by gabriella on 2010-06-13
I was wondering if any others have experienced this using GRUB2. Not too long ago I installed Karmic, which has GRUB2 by default, and this is when it started happening. It never happened before with Jaunty which used Grub legacy.

Sometimes when I boot up (but not always) instead of getting the GRUB splash I get a box which is the exact screen dimensions of the splash so it is obviously trying to load the splash screen. However, its full of coloured, dancing jigling square pixels thingies. Nothing readable at all. the only option is to switch off and try again which usually works. 

There have also been a few times where after Grub splash it's gone to a blank screen instead of booting.

Am I alone in experiencing this???????

---

### Post by hhoyt on 2010-06-13
U mite wanna check ur theme file.
/etc/grub.d/05_debian_theme

If looks ok, try installing a new theme and run 
sudo update-grub
It should detect your new theme.

ref: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
#8 Grub 2 Splash Images & Theming 

Cheers, Howard

---

### Post by gabriella on 2010-06-13
> **hhoyt said:**
> U mite wanna check ur theme file.
/etc/grub.d/05_debian_theme

If looks ok, try installing a new theme and run 
sudo update-grub
It should detect your new theme.

ref: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
#8 Grub 2 Splash Images & Theming 

Cheers, Howard

Thanks :)

That file looks OK but I don't quite understand what it would have to do with my problem? Can you explain how that could cause it? Probably 60-70% of the time it loads grub normally anyway.

Thanks G

---

### Post by garvinrick4 on 2010-06-13
You have "ureadahead" starting and "mountall" starting to mount your / and while that is going on your graphics drivers have to start your splash screen so it looks pretty while these other packages are getting your file system started up and X running.
Grub2 has done its job once you get to the point of selecting your disto and ureadahead starts running.
 Grub2 is not the culprit. Graphics driver maybe?

---

### Post by gabriella on 2010-06-14
> **garvinrick4 said:**
> You have "ureadahead" starting and "mountall" starting to mount your / and while that is going on your graphics drivers have to start your splash screen so it looks pretty while these other packages are getting your file system started up and X running.
Grub2 has done its job once you get to the point of selecting your disto and ureadahead starts running.
 Grub2 is not the culprit. Graphics driver maybe?

Good point! Searching around I do read about some issues with Nvidea which I belive my built in is. I have not installed any drivers apart from what installed by default from the CD. 

I admit I'm a little confused about this and how to proceed. System>Administration>Hardware Drivers list three proprietary Nvidea drivers but none are enabled. How do I check for what I need???

---

### Post by philinux on 2010-06-14
> **gabriella said:**
> Good point! Searching around I do read about some issues with Nvidea which I belive my built in is. I have not installed any drivers apart from what installed by default from the CD. 

I admit I'm a little confused about this and how to proceed. System>Administration>Hardware Drivers list three proprietary Nvidea drivers but none are enabled. How do I check for what I need???

Choose version current (recommended). Highlight it and then click activate. You have to reboot after it's installed.

---

### Post by gabriella on 2010-06-14
> **philinux said:**
> Choose version current (recommended). Highlight it and then click activate. You have to reboot after it's installed.

Thanks.

So do I need to remove something/what I have now first? Thats what I was previously told.

---

### Post by philinux on 2010-06-14
> **gabriella said:**
> Thanks.

So do I need to remove something/what I have now first? Thats what I was previously told.

Have you installed a graphics driver manually?

If it says in sys>admin>hardware drivers that no drivers are activated then just go ahead and activate the current version.

---

### Post by gabriella on 2010-06-14
> **philinux said:**
> Have you installed a graphics driver manually?

If it says in sys>admin>hardware drivers that no drivers are activated then just go ahead and activate the current version.

No..   As far as graphics are concerned just what installed from the live CD.  OK so I'll try one of Nvidea ones in listed in Hardware Drivers.
Thanks

---

### Post by philinux on 2010-06-14
> **gabriella said:**
> No..   As far as graphics are concerned just what installed from the live CD.  OK so I'll try one of Nvidea ones in listed in Hardware Drivers.
Thanks

Not any just the Version Current (recommended)

---

### Post by gabriella on 2010-06-14
> **philinux said:**
> Not any just the Version Current (recommended)

OK understood! I'm not at home right now but my memory is that there are three listed all with very different versions. Will check later..

---

