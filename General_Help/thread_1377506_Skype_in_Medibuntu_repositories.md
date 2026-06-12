---
title: "Skype in Medibuntu repositories"
date: 2010-01-10
forum: General Help
---

### Post by egruber on 2010-01-10
I believe I added the Medibuntu repositories properly, and I am told there is a version of Skype there. But when I search with Synaptic it doesn't show up.  All I get is Skysentials, python-skype, and skytools.

It was suggested that this version worked better than what was offered on the Skype website.

Any idea what I might be doing wrong?  Thanks!

---

### Post by spiderbatdad on 2010-01-10
No idea. However I believe you will not find the version in Medibuntu to work better than skype's latest beta 2.1.0.47.
What problems are you having? What system are you running skype on?

---

### Post by egruber on 2010-01-10
I'm running Karmic, but the Beta on the Skype website is for the previous version.  Audio works fine, and the video works fine until I call someone else with Video.  Then the videos either don't display, freeze or lag terribly.  I tried a side-by-side test using another laptop with Windows 7 and it worked perfectly.  So, it must be something with the Ubuntu version.

Any ideas?

---

### Post by Project PWNED on 2010-01-10
Installed the .deb file from Skype.com? dpkg -i then the file.deb to install it once you have it downloaded

---

### Post by egruber on 2010-01-10
> **Project PWNED said:**
> Installed the .deb file from Skype.com? dpkg -i then the file.deb to install it once you have it downloaded

I did download it from Skype.com, but I installed it by double-clicking on the deb file and Ubuntu did the rest.  Was I supposed to do something else?

BTW, I tried two versions since 3 are offered.  I tried the 32 bit version and the one with neither 32 or 64 bit specified.  Both had problems. I have an IBM Thinkpad T40.

---

### Post by minsf on 2010-01-15
i too was wondering where the skype package is. 
i cannot see it on [http://packages.medibuntu.org](http://packages.medibuntu.org) under karmic

---

### Post by mc4man on 2010-01-15
> i too was wondering where the skype package is.
i cannot see it on [http://packages.medibuntu.org](http://packages.medibuntu.org) under karmic
removed from medibuntu
[https://bugs.launchpad.net/medibuntu/+bug/494564](https://bugs.launchpad.net/medibuntu/+bug/494564)

---

### Post by minsf on 2010-01-16
thanks, this solved the mystery :)

---

