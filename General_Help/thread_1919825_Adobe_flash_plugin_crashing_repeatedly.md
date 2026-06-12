---
title: "Adobe flash plugin crashing repeatedly"
date: 2012-02-03
forum: General Help
---

### Post by crs501 on 2012-02-03
I presently use Ubuntu 10.04LTS with Firefox. This morning when I booted up I ran the Update Manager as usual and it indicated an upgrade available for Firefox (from the 9.0.1 I had to 10.0) so I completed the updates and went about my business. Immediately I noticed the Adobe Flash Plugin was crashing everywhere. I checked to be sure I was using the most recent Adobe Flash and I am - version 11.1.102.55 - so I then tried seeking help from Adobe Customer Support. The gentleman I spoke with suggested I seek help at forums.adobe.com but I found nothing of help there. I raised my question on Launchpad but while I'm waiting for a reply I decided to ask you guys here! 
I have heard of the plugin "flashaid" but when I tried to download it I got the message: "could not be downloaded because of a connection failure on 'addon.mozilla.org' so now I'm not sure what to try. I am not a programmer or developer, just a 62 yr old computer User with some limited knowledge & experience, so I might not fully understand any extremely technical responses. I am a drummer with a Country band and I go to YouTube frequently to learn songs, but now videos are unplayable, among the other problems a non-functioning Flash plugin presents. Any ideas? Please advise! Thanks, Richard...

---

### Post by ajgreeny on 2012-02-03
Try the flash-aid add-on again as it is probably the best answer.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search)
Perhaps that server was down earlier, but it is certainly working now.  When you have the add-on enabled, go to its Wizard Mode and try the Adobe beta version first, though be prepared to run it again and choose the stable version from the repos if the beta does not work.

The beta version is no good on my Lucid system, and just leaves an empty space where the video should be, but the version from the repos 11.1.102.55 is great.

---

### Post by crs501 on 2012-02-04
I did as you suggested, it WAS one of my first ideas anyway, and I still could not get it to download. Got the message "...could not be downloaded because of a connection failure on addons.mozilla.org". I've tried uninstalling and re-installing the most current Adobe Flash (11.1.102.55) several times but the issue persists. I'm wide open to more ideas. Just please realize I'm probably not as savvy as most of you so if you send me code or directions on how to use it, please explain simply and step-by-step and I will follow verbatim. Thanks!!! Richard...

---

### Post by crs501 on 2012-02-04
I see my browser going dark frequently and unresponsive here & there, it didn't do this til AFTER I upgraded to Firefox 10.0 when offered by the Updater Manager yesterday morning. Could Firefox be the problem and NOT Adobe Flash?

---

### Post by ajgreeny on 2012-02-04
> **crs501 said:**
> I see my browser going dark frequently and unresponsive here & there, it didn't do this til AFTER I upgraded to Firefox 10.0 when offered by the Updater Manager yesterday morning. Could Firefox be the problem and NOT Adobe Flash?
I suppose it could be, but I don't see why as I am running FF 10 on 10.04 Lucid without a problem.  Just as a test, try renaming the ~/.mozilla folder in your home as a backup and then start FF again to see if you can get flash-aid to work when using the clean profile.

---

### Post by crs501 on 2012-02-04
Sorry, I appreciate the tip, but I don't know how to do as you suggested. And I have to go to work now but I will be back online tomorrow after 12 Noon (Eastern time) to have another try. Thanks!

---

### Post by ajgreeny on 2012-02-04
> **crs501 said:**
> Sorry, I appreciate the tip, but I don't know how to do as you suggested. And I have to go to work now but I will be back online tomorrow after 12 Noon (Eastern time) to have another try. Thanks!
In you home folder there is a folder called .mozilla (note the . at the beginning of the name; that means it is normally hidden, so hit Ctrl+H when in file-manager to show it and other hidden files/folders).

Right click on it and choose Rename, then name it as .mozilla.bak.  Now start FF again, etc etc.

---

### Post by crs501 on 2012-02-05
Nope - - I did exactly what you said and Flash Aid still would not download. I've tried to download it several times and keep getting the message "...There was a problem downloading Flash Aid." I'm also trying to get some help over on LaunchPad. I'm open to all suggestions at this point!

---

### Post by crs501 on 2012-02-08
OK, I solved this myself, I simply backed up everything I needed to save, and re-installed Ubuntu 10.04. And in the process I now have no problem with my Adobe Flash Player anymore. I DID notice in installing Lucid Lynx I received a number of updates which in tandem with Firefox 10.0 have left me with an end result of my computer performing beautifully with (knock on wood) no performance issues at all!!! Thanks to everyone who tried to help!!!

---

