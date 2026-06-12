---
title: "multiple browsers &amp; flash"
date: 2010-06-10
forum: General Help
---

### Post by PsYcHoTiC_MaDmAn on 2010-06-10
previously when I tried having multiple browsers (then it was FF and flock) I briefly got flash working in both before it became completely borked (thing thats the best way of putting it)

right PITA to fix, and then only got it working in FF. I tried chromium a while back and whilst that had flash, FF wouldn't.

so considering multiple browsers means I have to be able to get them to work nicely. so any tips on getting several to work together

---

### Post by mkvnmtr on 2010-06-10
On my 9.04 install flash seems to be working fine on Firefox, Seamonkey , Chrome and Opera. All I did is install the restricted extras and flash and java works. I think I read somewhere that Chrome brings its own flash but the others use the regular flash plugin. On my 10.04 and Debian installs the same browsers seem to be fine also.

---

### Post by ubunterooster on 2010-06-10
add to sources in synaptic: [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu)

Then update

---

### Post by PsYcHoTiC_MaDmAn on 2010-06-10
this is an odd one.

installed chromium and opera, and flash works on all of them, but..... when I go to the Youtube homepage it crashes, it works on other youtube videos, but not the homepage

---

### Post by ubunterooster on 2010-06-10
in Firefox go to tools>addons>plugins>shockwave flash. what version is it?

10.0 r45 works fine for me

---

### Post by PsYcHoTiC_MaDmAn on 2010-06-10
theres 10.0 r45 and 10.0 d21

as its previously been. only happened after I installed opera.

I disabled r21 and it displayed the homepage, but gave a black box for video. re-enabled it (without disabling r45) and seems to have fixed itself

so odd bug, but not an issue.

on a side note, anyone have laggy performance with FF, ie sometimes loads pages instantly, othertimes it takes forever, but when it does connect page comes straight through (not bandwidth limited, I had been blaming this on my router, but doesnt seem to effect Opera or Chromium, I'd say bad install on this machine if it didnt also effect my notebook (but not on other networks) and also a windoze machine

---

### Post by PsYcHoTiC_MaDmAn on 2010-06-10
spoke too soon, d21 lets the videos play, but youtube homepage crashes....

I'll shove a line in on the Mozilla forums

ty for help

---

### Post by lovinglinux on 2010-06-10
> **PsYcHoTiC_MaDmAn said:**
> theres 10.0 r45 and 10.0 d21

as its previously been. only happened after I installed opera.

I disabled r21 and it displayed the homepage, but gave a black box for video. re-enabled it (without disabling r45) and seems to have fixed itself

so odd bug, but not an issue.

on a side note, anyone have laggy performance with FF, ie sometimes loads pages instantly, othertimes it takes forever, but when it does connect page comes straight through (not bandwidth limited, I had been blaming this on my router, but doesnt seem to effect Opera or Chromium, I'd say bad install on this machine if it didnt also effect my notebook (but not on other networks) and also a windoze machine

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html) for the loading page issue.

---

### Post by PsYcHoTiC_MaDmAn on 2010-06-10
> **lovinglinux said:**
> See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html) for the loading page issue.

TY, removed the conflicting modules, tis fixed. (though one command kept giving an abort regardless of whether I agreed or not)

though the loading one wasn't, I already had IPv6 disabled

---

