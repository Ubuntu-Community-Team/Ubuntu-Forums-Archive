---
title: "Firefox causing Xorg Crash - Goole image search"
date: 2010-10-18
forum: General Help
---

### Post by BrokeMahPC on 2010-10-18
Since Installing Lucid Lynx Ubuntu 10.04 I have had a Firefox problem.

Sometimes it would freeze and I had to minimise and maximize the window to get it working again.

Sometimes It would crash Xorg and leave me with a grey screen with black lines and I had to do a hard restart. Things improved but it was still occurring everytime I visited the Google search page and selected Images.

When the thumbs appeared it would stutter and freeze and if I scrolled up or down too rapidly it would crash Xorg to the 'grey screen of death'.

Just tried the following and it seems to have solved it. The scrolling is reasonably smooth and so far no crashes:
Override GPU validation
You can force the Flash Player to bypass its GPU validity checks. This can provide a considerable performance improvement in some situations and also fix some common fullscreen issues.

Code:
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > ~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

Found it here:
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

Variables: I am using the following Extensions, plugins and Compiz Fusion:
NoScript
Web Of trust (WOT)

VLC Multimedia Plugin
Shockwave Flash

Anyone else got any ideas on this? I will mark it solved if things continue to go well!

---

### Post by lovinglinux on 2010-10-18
Could be NoScript. It is crashing my Firefox 4 really bad on several sites.

---

### Post by BrokeMahPC on 2010-10-20
I did wonder about no-script but things are working fine now. Something that has also helped was deleting a swap partition on another drive.

I have 2 hard drives with several different Linux OS's and Windows.

I found the Linus OS's were using both swap partitions on both hard drives at once. I have made the smaller drive windows only and the larger one open source only which is neater and there is only 1 swap.

Things seem even better and more stable. Why? I dunno lol.

---

