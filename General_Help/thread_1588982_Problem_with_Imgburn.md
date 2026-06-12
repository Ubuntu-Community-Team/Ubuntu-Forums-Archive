---
title: "Problem with Imgburn"
date: 2010-10-05
forum: General Help
---

### Post by velzevool on 2010-10-05
I installed Imgburn yesterday and it worked fine.Today i open it and it says "No devices detected" which doesn't let me copy anything.

---

### Post by mc4man on 2010-10-05
Should be a simple fix - take drive detection away from wine - Open imgburn - tools - settings - I/O and switch the interface to the first choice - ASPI-WNASPI32.DLL
see screen

---

### Post by velzevool on 2010-10-05
Thank you very much,it worked.

---

### Post by milind_21_03 on 2010-10-20
Thanks for this fix. Now I have a different problem & I can't understand how to handle it.

I've tried burning .nrg CD images & I get the I/O Error attached in the screen-shot. I wasted 3 CDs but I still don't wish to give up.

Cheers for any help :-)

---

### Post by mc4man on 2010-10-21
> burning .nrg CD images
I believe it only supports 'single track, single session' .nrg's

You could install the trial linux nero and do your burning  or - 
a possible workaround.

Didn't have any .nrg's, -  so installed the nero trial and made an image from an audio cd (multitrack, single session, so no go in imgburn

[Installed CDEmu]("https://launchpad.net/~cdemu/+archive/ppa"), mounted the .nrg and then 'read' to a bin and cue w/ imgburn - see screen 1 (took about 30 secs to read/rip
 Then burned using the .cue - worked fine - screen 2

(Was also able to play the mounted .nrg in vlc

---

