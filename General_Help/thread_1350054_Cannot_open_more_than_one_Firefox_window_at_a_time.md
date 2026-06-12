---
title: "Cannot open more than one Firefox window at a time, tabs work fine"
date: 2009-12-08
forum: General Help
---

### Post by Robertjm on 2009-12-08
For the last few days I've ran into a really annoying issue with Firefox. At present I cannot open additional windows of Firefox, including using FILE|NEW WINDOW or using ctrl-N. However, I can open new tabs until the cows come home!!

Did a Google search and can't find any new articles on this problem. Anyone else experiencing this problem recently?

Robert

---

### Post by lidex on 2009-12-09
What version of Firefox would that be?
Are you using any tab extensions? Have you tried running with a new profile?
```
firefox -profilemanager
```

Make sure all firefox windows are closed before running above command

---

### Post by Robertjm on 2009-12-10
I created a new profile with profile manager and it DOES work, so there's something that is messing up my default profile.

Using version 3.5.5, which I got from the repositories.

Extensions currently using:
Delicious Bookmarks
FireFTP
Shorten URL
TwitterBar
Ubuntu Firefox Modifications package

Plugins:
Adobe Reader 9.1
DivX web player
Helix DNA Plugin
Quicktime
Shockwave Flash
VLC plugin
Windows Media Plugin

All are updated to the latest and greatest versions.

Thoughts?

---

### Post by lidex on 2009-12-10
First I would take a look at "about:config" in your regular profile and compare it to the new profile to see what, if any differences there are. Type "about:config" in location bar - no quotes - and in the filter field enter "window". If no help there, in your regular profile, disable all extensions and re-enable them one-at-a-time until you find the culprit.

---

