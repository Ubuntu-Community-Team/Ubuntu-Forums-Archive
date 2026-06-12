---
title: "Firefox problem, 9.04, same behaviour on 2 pc's"
date: 2009-06-29
forum: General Help
---

### Post by gardener on 2009-06-29
If I don't get a response here I'll try the Mozilla Firefox forums, but I thought I would try as I have two up to date Ubuntu 9.04 PC's that have the same issue with Firefox.

First, the suggest feature in the address bar becomes disabled during some sessions. Secondly, when this occurs, the "Search google for" button opens a new tab with Mozilla Firefox Start Page, instead of a google search with results. Thirdly, I have trouble copy and pasting when this occurs. This can spontaneously return to normalcy as well, it's done that just now. Everything that was disabled is now working properly. 


All 3 problems occur at once, at some point in a Firefox session. I have recently switched this PC to Ubuntu 9.04 from Linux Mint, but the other PC ran Heron for a year with no problems and then upgraded to 9.04 a month ago and this problem started occurring shortly after that. 

Took me a while to post as I searched around for a solution. It seems like it would be a common problem if it has occurred on both my machines, apparently after a flawed update. 


Thanks in advance,

gardener

---

### Post by beastrace91 on 2009-06-29
Try reinstalling firefox, or installing the 3.5 beta (which has been very stable for me thus far, the package name is firefox-3.5) I had the issue in my 3.0 firefox of the suggestion bar sometimes not working/hanging for a long while it appears to be fixed in 3.5 how ever, plus load times are way down.

~Jeff

---

### Post by michaelzap on 2009-06-29
I've also noticed that the "awesome bar" suggestions sometimes fail to pop up and copy and paste occasionally stops working. I've never noticed the Google results opening up a Firefox start page, however. I think that FF3 has some memory problems (since memory use climbs awfully high, and there are frequent CPU spikes whenever I have it open as well).

The official release of FF 3.5 is tomorrow, and soon after that it will be in the Jaunty repositories, so I'm just waiting to see if that fixes everything. I tried FF 3.5 beta on my desktop, and it does seem to be less of a hog. It has some minor theming glitches and not all my favorite add-ons worked with it yet, so I'm going to be patient a couple more days.

---

### Post by gardener on 2009-06-29
If this is fixed in 3.5 I'm sure I can wait for it to hit the repositories. Thanks for both responses.

---

### Post by lovinglinux on 2009-06-29
> **michaelzap said:**
> I've also noticed that the "awesome bar" suggestions sometimes fail to pop up and copy and paste occasionally stops working. I've never noticed the Google results opening up a Firefox start page, however. I think that FF3 has some memory problems (since memory use climbs awfully high, and there are frequent CPU spikes whenever I have it open as well).

Firefox problems are usually related to corrupted profile files, but they don't get fixed by their own, which makes me believe it's indeed a memory issue. I had this problem of awesome bar suggestions not popping up only once and momentarily.

If the awesome bar doesn't work at all, if bookmarks are missing or if you are unable to add new bookmarks, then deleting the file *places.sqlite* from the Firefox profile should fix the problem.

More about this and other troubleshooting solutions at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

> **michaelzap said:**
> The official release of FF 3.5 is tomorrow, and soon after that it will be in the Jaunty repositories, so I'm just waiting to see if that fixes everything.

It probably won't be in the repositories, just on Karmic Koala. Besides, such problems are usually profile related, so re-installing Firefox or getting updates won't fix the problem. An update might prevent further corruption of profiles, but once the profile it's corrupted, then the only way to fix it is to delete the profile itself or the corrupted file. Nevertheless, I think memory related issues will be improved, because Firefox 3.5 is much faster and responsive than 3.0.11.

---

