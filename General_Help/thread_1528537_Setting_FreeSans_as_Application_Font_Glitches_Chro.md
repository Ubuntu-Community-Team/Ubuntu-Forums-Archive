---
title: "Setting FreeSans as Application Font Glitches Chrome"
date: 2010-07-10
forum: General Help
---

### Post by Joseph Schwenker on 2010-07-10
I just set all of my fonts in Appearance>Fonts from Sans to FreeSans.  I noticed that when I did this, Google Chrome's omnibar had a glitch.  If I type, backspace, or try to select the text in the omnibar, the text seems to bounce up and down.  After determining that it was the "Application Font" setting that was causing the problem, since none of the other font settings affected Chrome, I decided to ask about this.  Is this a known issue?  Should I try using Chromium instead?

To reproduce:

Change application font from Sans to FreeSans
Open (restart if already open) Google Chrome
Hold down the a key while the omnibar has focus
Note the bouncing text

---

### Post by Joseph Schwenker on 2010-07-11
FreeSerif also has this problem.  Can anyone at least reproduce this issue?

---

### Post by Joseph Schwenker on 2010-07-11
bump

---

### Post by Joseph Schwenker on 2010-07-12
Come on!  86 views, and no one even TRIES to reproduce the problem?  Seriously, it's so simple!  All you have to do is run the steps listed above, then post if the result is the same.  PLEASE.

---

### Post by Joseph Schwenker on 2010-07-12
I have worked around the issue by setting my application font to Arial.  However, though Arial is similar to FreeSans, it is much closer in spacing, and is not free.  This is only a workaround.  Let's try to reproduce the bug, then report it to Google.  Can anyone help?

---

### Post by Joseph Schwenker on 2010-07-14
bump

---

### Post by chillicampari on 2010-07-14
Yep, it's really easy, not sure why no one has responded yet. I'm not using Ubuntu, but I can recreate it using Crunchbang 10 Alpha #1, Openbox. 

I *think* the DejaVu family is free, it might work out better than the Free* family (or Arial) for the time being. 

Edit- but I thought the default Sans is free too, so you'll want to check.

---

### Post by Joseph Schwenker on 2010-07-14
Excellent, I'll try that.  Thanks for responding; it's been really frustrating waiting.

---

### Post by Joseph Schwenker on 2010-07-14
I just tried it, but DejaVu Sans is pretty much a replica of Sans, which isn't want I want.  I want FreeSans.  Weird that Chrome glitches with it.  I keep thinking it's a size or placement issue; maybe some value hasn't been defined for how it fits into address bars?  Hmm, it's not that, because it works well with Firefox.  Maybe Chrome uses some weird address bar that isn't integrating well?  We should report this to the Chrome/Chromium development team.

---

### Post by chillicampari on 2010-07-14
If you file the report I can post a "me too", but my followup might be rejected (I'm using an alpha distro right now, based on Debian Squeeze but it's still labeled), not sure what their guidelines are. So, it might be better if at least one (or even better) two people confirm here on the forum using an official release distro. Maybe this thread will get more play to back up the report.

---

### Post by Joseph Schwenker on 2010-08-18
Yesterday, some updates to Ubuntu's fonts were released, as well as a new version of Google Chrome.  I am now able to use FreeSans without glitching Chrome.

---

