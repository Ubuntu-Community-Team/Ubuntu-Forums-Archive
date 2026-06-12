---
title: "Firefox favicons getting associated with wrong bookmark"
date: 2010-04-10
forum: General Help
---

### Post by GiveLove on 2010-04-10
Hello People, :)

I've had a minor, yet potentially embarrassing bug in Firefox 3.0.x for many months in Ubuntu 9.04, and just recently also experienced it with a fresh install of 9.10 with Firefox 3.5.x. 

Basically what happens is that occasionally a favicon will incorrectly be associated with a bookmark until I visit the bookmarked web site again. And these will be favicons from websites that I do not have bookmarked. Normally I wouldn't care. But if I was surfing porn, sometimes the porn site favicon would show up on one of bookmarks. Which could cause a bit of embarrassment. LOL 

It turns out through a bit of sheer luck, I discovered that the problem seemed to be a bug in the "Tab Mix Plus" Firefox add-on. Since I only wanted that add-on for it's last tab selected feature, I un-installed it and installed a much more light weight and simple add-on called "LastTab" to recreate that functionality. And I have yet to have this problem since then. 

I suppose it's possible that it could be an interaction problem between add-ons. So just for completeness of information, here's a list of all my add-ons prior to un-installing Tab Mix Plus and installing LastTab.

Adblock Plus
BetterPrivacy
Cookie Monster
Download Statusbar
FlashBlock
Tab Mix Plus
Print Preview
Ubuntu Firefox Modifications


I hope this helps some one. :)

GiveLove

---

### Post by lovinglinux on 2010-04-10
> **GiveLove said:**
> Hello People, :)

I've had a minor, yet potentially embarrassing bug in Firefox 3.0.x for many months in Ubuntu 9.04, and just recently also experienced it with a fresh install of 9.10 with Firefox 3.5.x. 

Basically what happens is that occasionally a favicon will incorrectly be associated with a bookmark until I visit the bookmarked web site again. And these will be favicons from websites that I do not have bookmarked. Normally I wouldn't care. But if I was surfing porn, sometimes the porn site favicon would show up on one of bookmarks. Which could cause a bit of embarrassment. LOL 

It turns out through a bit of sheer luck, I discovered that the problem seemed to be a bug in the "Tab Mix Plus" Firefox add-on. Since I only wanted that add-on for it's last tab selected feature, I un-installed it and installed a much more light weight and simple add-on called "LastTab" to recreate that functionality. And I have yet to have this problem since then. 

I suppose it's possible that it could be an interaction problem between add-ons. So just for completeness of information, here's a list of all my add-ons prior to un-installing Tab Mix Plus and installing LastTab.

Adblock Plus
BetterPrivacy
Cookie Monster
Download Statusbar
FlashBlock
Tab Mix Plus
Print Preview
Ubuntu Firefox Modifications


I hope this helps some one. :)

GiveLove

Yes its possible that the problem is due to the interaction of two extensions. I have 3 extensions under development that suffers from this problem. One was interacting with All-in-One-Sidebar, causing high CPU usage when closing the sidebar with my extension loaded. I couldn't find a solution, so I dropped the sidebar and started to launch the extension on a new window. 

The other two are similar extensions that interact with Web Developer extension. My extension compare checksums, but when running along with Web Developer, the hash number generated is appended by the first two digits making the verification impossible. Fixed that by adding a special option that strips the last two digits if the user has Web Developer installed.

The worst thing is that I have spend countless hours tweaking my code without success until I noticed the problem was absent on a clean profile :)

---

