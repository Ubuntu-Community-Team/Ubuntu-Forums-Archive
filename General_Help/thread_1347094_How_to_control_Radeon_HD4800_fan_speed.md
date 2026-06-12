---
title: "How to control Radeon HD4800 fan speed?"
date: 2009-12-05
forum: General Help
---

### Post by ds9voy on 2009-12-05
Hi everyone,

I am new to Linux moving from Windows.

On Windows in the ATI control center you could control the fan speed on the video card.

I managed to figure out how to install the ATI control center.... or so I thought.  I did it through the Ubuntu Software Center, but when I click on the ATI control center link in Applications nothing happens.... no control center opens.

Is the fan control even if the ATI control center on Linux, or is there another way to change the video card fan speed?

Thanks for any help!

---

### Post by robobot on 2009-12-05
Last I checked, this feature hasn't been implemented in the Catalyst Control Center for Linux yet. 

However, you may be able to do it through the command line. Open a terminal and type ```
aticonfig --help
``` and then read through the list of available settings.

---

### Post by repilce on 2009-12-07
New user to 9.10 as well with a 4870 card. I used the Provided Tested driver that ubuntu offered , These cards get really hot with bios settings at almost NO fan speed until 70C+.

I hope AMD/ATI gets on this issue soon.  

The aticonfig --help provided a TON of options. so much that i could not scroll up to where i typed the command *sigh

Alternatively if your one to "mod" anything, you could take a VR and throw it into your 5V/12V rail and just set at a level comfortable to your ears. Something i will most likely have to resort to once i see if caldega works as i would want with wow.. then I shall give up the Win-bomb.  :cheers:

---

### Post by frito on 2010-10-31
There is a lot of stuff that isnt in the help file.

This guy figured out how to modify fan speed.
[http://forums.fedoraforum.org/showthread.php?p=1386622]("http://forums.fedoraforum.org/showthread.php?p=1386622")

---

