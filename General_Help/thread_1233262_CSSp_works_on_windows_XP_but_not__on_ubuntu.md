---
title: "CSSp works on windows XP but not  on ubuntu"
date: 2009-08-06
forum: General Help
---

### Post by zarthon on 2009-08-06
I am tring to figure out what is causing this bug. 
It concerns me because i also design pages and wish to target Firefox on Ubuntu but sometimes test on the Windows version of firefox.
I'd be happy if someone else was curious and wanted to help figure out if where a bug should be posted. - comcast, ubuntu or firefox


Problem:
Menu items in some drop downs work on firefox on windows xp but do not on ubuntu. An example is comcast.com. ( see large screenshot with more version info and dropdowns.) This is actually the only example of this difference i have found but manybe others have found more or know of a bug. Also I may be missing a bug from my attempted searches on bugzilla for firefox.

comcast could have css javascript html or server side code conditional on operating system. i have yet to inspect the code in detail.

System factors:
ubuntu version is 3.0.12 and windows xp version is 3.0.13
ubuntu install is 64-bit 9.04 and windows xp is 32 bit with latests updates.
The two systems use a similar but not identical set of plugins

i am going to try updating firefox. I now see there is an update in the pipeline.
I am also going to try without any plugins to see if the problem is with a plugin i am using.

Screen shot using rdesktop is attached. 
The page url is:
[http://www.comcast.com/shop/buyflow2/products.cspx?SourcePage=Cable](http://www.comcast.com/shop/buyflow2/products.cspx?SourcePage=Cable)

---

### Post by zarthon on 2009-08-06
Indeed the problem is with a plugin / extension
:-D
I guess that this information may help someone looking for what's wrong with there browser so i will leave it up.

I have a noextensions profile for testing my own pages and this displayed the page properly using the same version of Firefox and Ubunutu.

---

