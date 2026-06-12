---
title: "Message display issue in Thunderbird 3.1 - package vs. standalone"
date: 2010-08-06
forum: General Help
---

### Post by gintan on 2010-08-06
Hi There,

I'm having a rather strange problem with Thunderbird 3.1 (although I was running 3.0.6 when the problem actually started) on Ubuntu 9.10.  Some messages appear completely blank except for the quote indicators (ie. the vertical lines next to the left margin to show the reply context) but otherwise empty.  Even 'view source' shows blank - although I can scroll down for a considerable time as if there is content in there.

In terms of remedying it, I have gone through the various processes of trying to repair corrupted folders etc. but with no effect.  Here's the strange thing though - I uninstalled Thunderbird and then downloaded the standalone version from the Mozilla site.  With the same mailbox files, the standalone works fine and displays the messages that weren't displayed in the version installed as a debian package.

I'd rather not use a standalone mail client though.  Can anyone point me in the right direction on this one?  I suspect it might have something to do with fonts.  Also because the only changes to the system I've made recently were installing fonts and rebuilding the font cache.

Cheers

Greg

---

### Post by DeMus on 2010-08-06
With standalone version you mean a version downloaded form the Mozilla site, or, like I did, download it and just extract it into the home directory and don't install it, just use it?
I extracted the downloaded file and did not install it. In the folder where I extracted everything into is a file called thunderbird, that's the one I start, works great.
You write you installed fonts. Can it be you are using a white font on a white background? I know it's a stupid question, but please check it. It wouldn't be the first time somebody has had this.

---

### Post by gintan on 2010-08-06
Sorry yes, I just downloaded the .tar.bz2, unzipped it in my home folder and ran it from there without installing it.

Oh crap, you were right!  I just tried selecting everything in the message and pasting it into a text file and the whole message is there.  Then I changed all the fonts back to the defaults in edit->preferences->display-advanced and everything is displaying correctly. Can't believe I wasted so much time on this!

Thank you!

---

### Post by soldier1st on 2010-08-06
if you have the solution to your problem then mark your thread as solved.

---

### Post by gintan on 2010-08-06
Aye, aye sir.

---

