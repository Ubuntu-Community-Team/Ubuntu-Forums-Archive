---
title: "Tvbythenumbers crashes firefox"
date: 2010-05-30
forum: General Help
---

### Post by sddfdds on 2010-05-30
The problem is random but reproducible: go to [http://www.tvbythenumbers.com/](http://www.tvbythenumbers.com/), navigate around for a while, click some links...eventually firefox (3.6.3 on 10.04) will crash.  I tried running firefox from the command line, but all it says is 'Segmentation fault' with no details.  What can I do to diagnose this?

---

### Post by lovinglinux on 2010-05-30
Check if you have libmoon installed and remove it. It is causing such crashes when viewing flash content.

If you don't have it, then see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Also using [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/) might help.

BTW, that site doesn't crash here. Perhaps you could be more specific and provide a direct link to the page that makes Firefox crash.

---

### Post by MCVenom on 2010-05-30
Went on, clicked around, even did a search and tried some ads... No crashes here. :p

Running Firefox 3.6.3 on Lucid: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3

---

### Post by Pyrophorus on 2010-06-07
I get the same,but its more random on all kinds of sites.

---

