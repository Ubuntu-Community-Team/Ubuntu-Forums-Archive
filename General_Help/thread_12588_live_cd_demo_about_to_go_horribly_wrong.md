---
title: "live cd demo about to go horribly wrong"
date: 2005-01-25
forum: General Help
---

### Post by blackburnrovers on 2005-01-25
i see the ubuntu splash screen just fine. my resolution is set to 1024x768, fine. i hit enter, i see some kernel messages and then:
"You passed an undefined mode number
Press <RETURN> to see video modes available, <SPACEA> to continue or wait 30 secs:

If i hit return, i see "Video adapter: VESA VGA" and then a whole list of various modes for it in the format of:
"0   0F00   80x25" etc.

no matter what i choose, i see "welcome to morphix liveCD" but then get stuck with the following:
"Warning: unable to find base module!
Can't find Morphix filesystem. sorry
Dropping you to a busybox shell
Make sure you have a Morphix Base image on your CD-ROM/HDD/NETWORK devices
Press reset button to quit."

I am then at the "morphix#" command prompt with the BusyBox shell i think.

help would be GREATLY appreicated. i received a stack of CD's in the mail yesterday, and will be giving them out at a tech directors meeting if i can get them to work.

---

### Post by zogger on 2005-01-27
*don't * hit enter when you get to that prompt, you don't need to, and it's a definite useability annoyance to most people I would bet. It looks so important and all you just want to enter all sorts of details that have little to nothing to do with what you really want to do, get it to finishi booting. Ignore it. Just wait for it to finish booting normally or hit the spacebar instead to bypass it. Got stuck there, too, until I tried to ignore it, and THAT worked.

I'm having other issues, but that one I figured out.

---

### Post by blackburnrovers on 2005-01-29
[QUOTE=zogger]*don't * hit enter when you get to that prompt, you don't need to, and it's a definite useability annoyance to most people I would bet. It looks so important and all you just want to enter all sorts of details that have little to nothing to do with what you really want to do, get it to finishi booting. Ignore it. Just wait for it to finish booting normally or hit the spacebar instead to bypass it. Got stuck there, too, until I tried to ignore it, and THAT worked.

I'm having other issues, but that one I figured out.[/QUOTE]

even when i don't hit anything, i get to the same point as above. i think it is a hardware incompatibility issue with my Dell Latitude D400. My D600 works just fine. I also run into the same problem with a C400.

---

### Post by jemini on 2005-01-30
Actually I have the same exact problem. Running a Dell Latitude C400, does the whole screen thing....
although i tested it on a D400 and it worked fine...  :cry:

---

