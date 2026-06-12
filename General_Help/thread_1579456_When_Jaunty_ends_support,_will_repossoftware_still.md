---
title: "When Jaunty ends support, will repos/software still be available?"
date: 2010-09-21
forum: General Help
---

### Post by CanadianPenguin on 2010-09-21
It's come to my attention that support is ending for 9.04 next month, which I am still running.

I'm somewhat fine and dandy with this, but I have a few concerns about support for Jaunty ending:

When support ends for 9.04, will the repositories still be available for Jaunty, and will software meant for Ubuntu but made after 9.04's end of life be available for Jaunty?

I refuse to upgrade because:

[LIST=1]
[*]**I'm using Wubi, and last time I tried to upgrade a Wubi installation it corrupted itself.** The reason I'm running Wubi is because Winblows randomly stopped booting and Vista's infamous black screen of death is pretty much unfixable since nobody knows the real cause of them. By chance, I had a Wubi install of Ubuntu Jaunty I had previously used for testing out the OS but forgot to remove - and it worked. I'm using it until I get a 1tb external hard drive to back everything up to and factory reset my computer - and that probably won't be for a while. Part two: After my younger sister complained about her Dell Mini being slow as hell in factory condition, I installed Wubi onto it as a test run to see if she thought Ubuntu worked good. It worked greatly, and she didn't really know the difference between Wubi/dual boot, so I saw no reason to dual boot it. And some time later, she saw the cool-looking Lucid Lynx and told me to upgrade it. I installed 9.10 and it said it would reboot. Left it overnight and it was still on the Jaunty desktop. Tried clicking on the shutdown button again but it did nothing. Every other menu/button did nothing as well, though it displayed the animation as if it was being pressed. I hard reset the computer after the ctrl-printscreen-whatever combination didn't work, and upon turning it on I was dropped at the Linux command line because the GUI failed to appear. I didn't know what to do and couldn't find any fix for this, so I copied her home directory to her Windows install and reinstalled Wubi - using Lucid Netbook this time. Since this computer I'm on has tons of important data on it and Wubi is the only thing making it usable, I don't want to try upgrading if it was a colossal failure that was advertised as working.
[*]**I like Jaunty. **I don't really have any problems with Jaunty and think it's fine how it is. It works great, it's fast, it doesn't have tons of unnecessary flashy decoration crap contained in Lucid, and it was also the first version of Ubuntu - and any Linux distro - so I've grown pretty used to it.
[*]**Jaunty is the last/only version that didn't give me hell. **Upon trying Karmic and Lucid on my our desktop/sister's laptop, respectively, they were filled with piles of problems and broken crap. I never managed to get my sound/wireless working on Karmic, and it took me solid hours to get it working on Lucid, and I don't even know how I did it. Not only that, but a lot of the default programs don't work/are completely useless. These are not Wubi-specific problems since a quick Google search on them confirms these.
[/LIST]
So, can I keep my precious 9.04 or will I have to tempt fate and upgrade to Maverick when Jaunty meets its demise?

---

### Post by zvacet on 2010-09-22
Of course you can keep Jaunty,but what it comes to the end of life you will not get any security updates.I don´t think it is good option,but it is your decision.

---

### Post by snowpine on 2010-09-22
As with all previous Ubuntu releases, when Jaunty reaches end-of-life, its repos will move to old-releases.ubuntu.com, and you may update your Software Sources accordingly. Of course, these repos will no longer be updated or officially supported in any way, so you will not receive any updates, security patches, or bug fixes. Furthermore, most 3rd-party software developers do not package their applicataions for end-of-life releases; as an example I tried to install Boxee on a Jaunty machine yesterday and discovered it is no longer supported.

---

### Post by jmszr on 2010-09-22
CanadianPenguin,

Here is a link re: setting up your Software Sources for old-releases.ubuntu.com:  [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143) .

You might want to update to Lucid instead of Maverick as Lucid is LTS and will be supported for 3 years.

New software is really hit-or-miss, as I've found with Hardy. A few are backported but tracking down and installing the various dependencies/libs etc. for the rest is a real PITA, if possible at all.

---

