---
title: "Using csplit with html files"
date: 2012-01-16
forum: General Help
---

### Post by MeKino on 2012-01-16
Hi,

I have several html files which have sections divided into chapters thus:

<h3>Chapter 1</h3>
<p>some text</p>
<h3>Chapter 2</h3>
<p>some more text</p>
<h3>Chapter 3</h3>
<p>no more text after this</p>

and I have been trying to use csplit in the form:

csplit -z filename.html /Chapter/ {*}

but it doesn't work - it's not picking up the separate Chapters.

I suspect it's because of the <> markers but I've been trying to no avail so far.

Does anybody have an idea how this could be done?

Thanks in advance.

---

