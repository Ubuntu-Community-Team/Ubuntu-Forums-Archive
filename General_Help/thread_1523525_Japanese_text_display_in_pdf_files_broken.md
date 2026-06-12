---
title: "Japanese text display in pdf files broken"
date: 2010-07-03
forum: General Help
---

### Post by Yuri sss on 2010-07-03
This is for Lucid 10.04 x64.

When opening pdf files that contain Japanese text, the Japanese text *is not displayed at all*. Ordinary western text is displayed normally.
The Japanese fonts in all pdf files are an "embedded subset", i.e. Japanese text should display fine even if Japanese fonts were not installed (they *are* installed).
Japanese text works fine everywhere else: in plain text files, in Firefox etc. Typing Japanese works fine, too: &#28779;&#12398;&#12365;&#12388;&#12397;&#12395;&#12399;&#12289;&#26085;&#26412;&#35486;&#12398;&#12486;&#12461;&#12473;&#12488;&#12364;&#22823;&#19976;&#22827;&#12391;&#12377;&#12290;
Curiously enough, the thumbnail preview of the pdf files in Dolphin does show the Japanese text properly.

The problem exists independently from the pdf viewer used, it's the same with Okular (Kde 4.5 RC 1) and evince (2.30), both don't display Japanese text in pdf files.

Here's an example of how it *should* look: (screenshot taken in a different distro)

[[IMG]http://img228.imageshack.us/img228/5615/pdfjapanesecorrect.png[/IMG]](http://img228.imageshack.us/i/pdfjapanesecorrect.png/)

Here is a screenshot of how it *actually* looks: (the same in Okular and evince)

[[IMG]http://img816.imageshack.us/img816/9117/pdfjapanesebroken.png[/IMG]](http://img816.imageshack.us/i/pdfjapanesebroken.png/)

I've already tried reinstalling the pdf viewer, but as expected, that didn't change anything.
How do I fix this and get Japanese text in pdf files properly displayed? I need it for university, so it's important.

---

### Post by happyhamster on 2010-07-03
Try installing the package "poppler-data" and/or "xpdf-japanese".

Good luck.

---

### Post by Yuri sss on 2010-07-04
> **happyhamster said:**
> Try installing the package "poppler-data" and/or "xpdf-japanese".

Good luck.

The description of "poppler-data" in Synaptic already sounds promising:
> Encoding data for the poppler PDF rendering library

This package contains the encoding data needed to view some PDF documents with libpoppler.

**If CJK users want to view PDF files that contains their language, this package will help**, such as cmap-adobe-{gb1,cns1,korea1,japan1,japan2}.

I installed it and the cmap-adobe files it mentioned, and now Japanese text works fine =D> Thanks!
They really ought to have these packages installed by default.

*Edit:*
Marked thread as "Solved".

---

