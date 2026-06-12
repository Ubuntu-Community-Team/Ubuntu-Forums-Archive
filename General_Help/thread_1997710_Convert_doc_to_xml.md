---
title: "Convert doc to xml"
date: 2012-06-05
forum: General Help
---

### Post by anemone42 on 2012-06-05
I have a bunch of doc documents (Microsoft Word, not docx, can't open in archive manager). I want to convert them to xml, batch style.

It is important that the xml document contain info about:

[LIST]
[*]all the text
[*]new lines
[*]tab
[*]styles like
[LIST]
[*]small capitals
[*]italics
[*]bold
[/LIST]
 
[/LIST]
Other than that, a not too complicated xml format.

Any suggestions?

---

### Post by HermanAB on 2012-06-05
You can run Libre Office Writer from the command line to do that.  Go to their web site and have a look around.

---

### Post by anemone42 on 2012-06-05
Okay, it seems this is on the right track.

```
$ libreoffice --headless --invisible --convert-to xml test.doc
```My guess is I will have to twiddle either the infilter or the outfilter to keep all the formatting.

New line is preserved, so is all the text. Tab is converted into a couple of spaces. Small caps, bold and italics is just lost.

So, any suggestions for what I should use as filters (in and out) are welcome.

---

