---
title: "I screwed up my ubuntu, semms to some sort of 'radeon' problem."
date: 2011-06-22
forum: General Help
---

### Post by pitaj on 2011-06-22
Hey guys, just signed up for ubuntu forums because I couldn't find an answer myself.  I have an HP Pavilion dv7 dual booting ubuntu 11.04 and Windows 7 HP via Grub.  My system was working fine, ubuntu booting up, everything just fine, until i accidentally forgot i was in suspend and removed my battery.  Lost my suspend.  I started it up, Grub booted, everything looked fine, except I got stuck at a completely blank screen every time I tried to start ubuntu.  Windows is unaffected.  I can boot up my Live CD.  I started it with verbose and got this:

[Pic 1]("https://mail.google.com/mail/?ui=2&ik=0540df57ec&view=att&th=130ba23005244ab9&attid=0.1&disp=inline&zw")
[Pic 2]("https://mail.google.com/mail/?ui=2&ik=0540df57ec&view=att&th=130ba23005244ab9&attid=0.3&disp=inline&zw")


I really want my ubuntu back guys, thanks.

---

### Post by flipper T on 2011-06-22
why have you hyper linked to a gmail account?

---

### Post by SoFl W on 2011-06-22
Whatever picture you are trying to link to wont show.  There is a "manage attachments" under the message box when entering a message.

Have you tired the (recovery mode) option when you get to grub?  It is under the ubuntu selection that you usually use.

---

### Post by life in color on 2011-06-23
Do you have a recovery mode for Ubuntu? I would advise you to try that.

---

### Post by wildmanne39 on 2011-06-23
> **pitaj said:**
> Hey guys, just signed up for ubuntu forums because I couldn't find an answer myself.  I have an HP Pavilion dv7 dual booting ubuntu 11.04 and Windows 7 HP via Grub.  My system was working fine, ubuntu booting up, everything just fine, until i accidentally forgot i was in suspend and removed my battery.  Lost my suspend.  I started it up, Grub booted, everything looked fine, except I got stuck at a completely blank screen every time I tried to start ubuntu.  Windows is unaffected.  I can boot up my Live CD.  I started it with verbose and got this:

[Pic 1]("https://mail.google.com/mail/?ui=2&ik=0540df57ec&view=att&th=130ba23005244ab9&attid=0.1&disp=inline&zw")
[Pic 2]("https://mail.google.com/mail/?ui=2&ik=0540df57ec&view=att&th=130ba23005244ab9&attid=0.3&disp=inline&zw")


I really want my ubuntu back guys, thanks.Hi, post the information from this script and we can see how to help you. You will need to boot from the livecd to do this procedure.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by pitaj on 2011-06-23
I had to post this from my phone so I couldn't upload pictures.  I've tried recovery mode and everything, the verbose boot says a whole bunch of lines ending with "[radeon]".  The last line before the blinking cursor that does nothing is this:

[   22.413277] ---[ end trace 188659cc2ffafbdd ]---

Also, I can't use any kernel command at all, no hotkeys, just nothing.

---

### Post by wildmanne39 on 2011-06-23
> **pitaj said:**
> I had to post this from my phone so I couldn't upload pictures.  I've tried recovery mode and everything, the verbose boot says a whole bunch of lines ending with "[radeon]".  The last line before the blinking cursor that does nothing is this:

[   22.413277] ---[ end trace 188659cc2ffafbdd ]---

Also, I can't use any kernel command at all, no hotkeys, just nothing.
Hi, ok go to this link and follow the directions then you should be able to boot.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by pitaj on 2011-06-23
> **wildmanne39 said:**
> Hi, ok go to this link and follow the directions then you should be able to boot.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I just did this and it worked (thank you so much!!) so now what do i do to get unity back?

---

### Post by wildmanne39 on 2011-06-24
> **pitaj said:**
> I just did this and it worked (thank you so much!!) so now what do i do to get unity back?Hi, ok after you booted did you check to see what the problem is like your video driver most likely got corrupted so you if thats the case you should uninstall it and reinstall it. I am not 100 percent positive that is the cause but I it is most likely. See the steps you did I believe are just to get you to boot once, so you can fix your problem, unless you follow the guide and made it permanent. Did you make the setting permanent? We need to make sure you can boot every time and not just once before we try to fix unity, but if it is your video card driver, then reinstalling it will probably fix unity and the boot problem for good.

---

### Post by pitaj on 2011-06-24
> **wildmanne39 said:**
> Hi, ok after you booted did you check to see what the problem is like your video driver most likely got corrupted so you if thats the case you should uninstall it and reinstall it. I am not 100 percent positive that is the cause but I it is most likely. See the steps you did I believe are just to get you to boot once, so you can fix your problem, unless you follow the guide and made it permanent. Did you make the setting permanent? We need to make sure you can boot every time and not just once before we try to fix unity, but if it is your video card driver, then reinstalling it will probably fix unity and the boot problem for good.
Ok i have boites a couple times with nomodeset, and that's the only thing that seems to work.  I have not made it permanent.  I haven't tried uninstalling or reinstalling any drivers yet but I will.

Thanks again though!!

---

### Post by pitaj on 2011-06-24
I tried purging and reinstalling the radeon and ati drivers but to no avail, i still get that same error message!

---

### Post by pitaj on 2011-06-24
and here are the pictures of the last screen in verbose:

---

### Post by wildmanne39 on 2011-06-24
Hi, ok well we know that the driver can work because  it was working before the suspend issue. Do you have look in synaptic and make sure you do not have two drivers installed if you do right click and mark for complete removal. Also I am going to give you a link for installing video drivers, if you have to you can make the boot setup permanent but without the driver you wont have unity or good graphics.
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

---

### Post by pitaj on 2011-06-28
What could be the other driver?  The one i should uninstall?

---

