---
title: "n00b help..."
date: 2010-01-29
forum: General Help
---

### Post by smashweights on 2010-01-29
first off i wanna say i know jack **** about linux/ubuntu and am just starting to try this out as an OS.  I had 9.04 working on my compy when i installed today and then it updated to 9.10.  now when i load up my screen flashes white/black and never loads the GUI.  I had this problem initially with 9.04, but i used the recovery mode to access a "fix graphics something or another" and it loaded the GUI (9.04) just fine.  The new (9.10) recovery mode doesnt give me this graphical fix option anymore and i'm stuck in either a command prompt or a flashy, attempting to load GUI state and can't escape.

i have searched high and low, but my non-existent linux knowledge base makes interpreting most forum help impossible.

I'm running an ATI X800 running S-video and HDMI to my TV.  The S-video because it would never display the boot sequence stuff over HDMI, but will on the S-video and the HDMI kicks in once the GUI loaded.

---

### Post by smashweights on 2010-01-29
no ideas?

---

### Post by ShadowWraith on 2010-01-29
Do you have regular integrated graphics as well as your ATI card?

If so, try removing the card and running the computer on it's regular graphics. If it works, that means the problem is with your graphics drivers. If it doesn't, then you probably have a problem with your ubuntu installation.

If the problem is with the installation, then a file backup and reinstall is probably the best option. Otherwise, you will have to get your graphics drivers working properly. I don't know much about ATI cards, but this is ATI's official driver download for your card.
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English)
There should also be an official ubuntu driver for your card.

---

### Post by smashweights on 2010-01-29
no, i've only got the graphics card. how do i even get drivers/etc without the GUI?  i do not have a dual install right now, using my roommates mac...

---

### Post by ShadowWraith on 2010-01-29
See above for the official driver download.

The ubuntu driver package for your card seems to be xorg-driver-fglrx .

Does your system throw any error messages when it boots? Perhaps that will narrow the problem.

---

### Post by dBuster on 2010-01-29
There is a thread dedicated to this issue as many seem to be having.  Search out 9.10 and flickering screen and you should see the postings.  There are solutions to get your gui desktop back.

Okay so maybe those search terms wont work...  Just tried to get the posting for you.  I know there is one as I read it as I am preparing to possibly take the plunge up to 9.10 on the main laptop...  Kind of liking it on the netbook...

Try searching for it though, a little searching will result in a nice long thread about it...

---

### Post by smashweights on 2010-01-29
no error codes, it seems most of the threads deal with flickering within the GUI?  there's no colors or anything and it doesnt even get to the Ubuntu load bar.  is there anyway in 9.10 to get to that alternative graphics option, like 9.04?

---

### Post by smashweights on 2010-01-29
is 9.10 more finicky?  if it'll be less of a hassle in the long term to just stick with 9.04, i'll just revert back.

---

### Post by screaminfakah on 2010-01-29
You could try this from the command line in the recovery console.

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

---

