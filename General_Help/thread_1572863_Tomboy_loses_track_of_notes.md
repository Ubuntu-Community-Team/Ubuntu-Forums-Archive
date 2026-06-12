---
title: "Tomboy loses track of notes"
date: 2010-09-11
forum: General Help
---

### Post by Halfwalker on 2010-09-11
Strange problem here ... Tomboy is missing some of the notes.

Ubuntu Karmic x64, up to date. I noticed that some notes were missing, and went searching. Lo, the files are in ~/.local/shared/tomboy, but some of them are not being seen or read by Tomboy.

I've removed and added it back to the panel, to no avail. How does Tomboy index or read the notes files ? I have edited some of them manually now and then, when I was away from the box and ssh'd in.

There is probably a syntax error or something n those missing ones, but I haven't been able to find it/them.

Any ideas ?  How can we enable logging or debug output ?

D.

**SOLVED**
Simple problem ...  I had added a couple of URLs to the missing notes.  They included an ampersand char in them that was not escaped as it would have been had it been added in via the Tomboy interface.

Once I replaced the & with an &amp; and restarted Tomboy, they showed up just fine.

---

