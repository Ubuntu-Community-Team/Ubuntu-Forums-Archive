---
title: "karmic, firefox googlebar-lite problem"
date: 2009-11-01
forum: General Help
---

### Post by ajgreeny on 2009-11-01
I am trying karmic, not without a few problems, such as the driver issue with an ati 9200SE card and lack of desktop wallpaper, which is sort of solved for the moment, but also in Firefox 3.5.4, I can not get the add-on **googlebar lite** to show in any form at all.  There were also a few other add-ons that would not show, nor work, with the **ubuntu firefox modifications** add-on running, so I have disabled that, but I can not get googlebar-lite to show in the toolbars at all, in spite of the box being checked.  I have tried both with and without compiz running, so it is not related to that.

Anyone have any ideas?  So far I am finding this version a little more difficult to get running as I like it than I did jaunty, but this is just a separate partition I use for testing distros, and I still have Jaunty running smooth as silk as my main OS, so mustn't complain too much, but I had great hopes for this new one and so far have been somewhat disappointed.

EDIT:  Problem solved.  The whole difficulty was caused by a corrupted profile.  I was previously running FF3 in Jaunty, and simply copied over the old ~/.mozilla folder to Karmic for use in FF 3.5, but obviously the system did not like that at all.

Then back in jaunty I installed FF 3.5 from the jaunty repos and then copied the profile from the firefox-3.5 folder contained in jaunty's ~/.mozilla folder.  This time everything worked.  Thank goodness; I find it very difficult to work without googlebar lite these days.

---

