---
title: "Need a TIFF viewer that can handle multiple pages."
date: 2010-05-08
forum: General Help
---

### Post by BFG on 2010-05-08
I have a fax-to-email service which delivers files in multi-page tiff format.  Ubuntu image viewers only show page 1.

I found [ghfaxviewer]("http://packages.ubuntu.com/jaunty/ghfaxviewer"), which is apparently a perfect tool for this, but as of Karmic it's no longer in the repos.
[https://bugs.launchpad.net/ubuntu/+source/ghfaxviewer/+bug/468239](https://bugs.launchpad.net/ubuntu/+source/ghfaxviewer/+bug/468239)

Does anyone know of an alternative?  Preferably in a repo somewhere.

---

### Post by davidmohammed on 2010-05-08
never used it myself - but sffview is a package you may want to look at

---

### Post by ewz on 2010-05-08
I'm pretty sure Evince opens Multipage tiffs

---

### Post by ewz on 2010-05-08
Just tested it Evince does opem multipage tiffs (Right click on the tiff - Open With and select **Document Viewer**) 

Hope this Helps :)

---

### Post by BFG on 2010-05-10
Many thanks ewz, that worked for me :)

---

### Post by AlexanderDGreat on 2011-05-16
Thank you for this!

Just to state my purpose for this.

Because I can't find a decent modem that works for Ubuntu,

I used Windows XP - fax machine to receive faxes and saves to a folder C:\faxes. Then I use AutoMailer (freeware) to poll and send through email the folder C:\faxes, but it's in TIF format.

So Evince does the job pretty well. :)

---

