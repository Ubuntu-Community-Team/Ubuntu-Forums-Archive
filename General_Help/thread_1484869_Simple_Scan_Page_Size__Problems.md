---
title: "Simple Scan Page Size  Problems"
date: 2010-05-16
forum: General Help
---

### Post by jadymitchell on 2010-05-16
I was very excited about the inclusion of Simple Scan in Lucid.  A nice frontend and dead simple.

The big problem for me, though, is setting the page size.  I explicitly tell SS that the document is letter size and it insists upon outputting a legal size document.  If I switch the size to auto, I get the same result.

I saw an old Launchpad bug about having to crop the page, but surely the user can't be expected to crop numerous pages just to output a proper sized pdf!

Any suggestions?

---

### Post by justin.waters on 2010-05-16
No suggestions, but I'm having the same problem.  I have about 30 documents to scan, and I really don't feel like having to crop every single page...

---

### Post by justin.waters on 2010-05-16
Ooh, good news.  Simple scan seems to remember your crop settings for multipage documents.

[LIST=1]
[*]Scan the first page
[*]Select: Page->Crop->Letter
[*]Adjust the crop box to fit your scanned area
[/LIST]

Every page that you scan in the remainder of this session will be cropped accordingly.

It's not really intuitive, though.  The fact that the Preferences->Page dialog doesn't work tells me that this is not the preferred way to handle this, and that there is a bug in there somewhere.

EDIT:  Spoke too soon.  Looks like all of my documents are HUGE, and evince thinks that they are 35x45 inches!  This isn't as "simple" as it should be...

---

### Post by jadymitchell on 2010-05-16
Oh well, I guess it's back gscan2pdf which, after all, is a perfectly good program.

---

### Post by HughR on 2013-02-04
This problem is probably related to [http://ubuntuforums.org/showthread.php?p=12492798]("http://ubuntuforums.org/showthread.php?p=12492798")

---

### Post by varunendra on 2013-02-04
Old thread closed.
Please do not bump threads that are too old. From Forums CoC-
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

