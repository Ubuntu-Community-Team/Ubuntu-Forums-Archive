---
title: "Making LibreOffice documents beautiful"
date: 2012-06-20
forum: General Help
---

### Post by ubiquitin.jf on 2012-06-20
I've recently started working on my masters' dissertation in LibreOffice (+ Bibus for referencing, LOVE the PubMed search function) but am dissatisfied with the quality of the documents it outputs. The fonts aren't smooth or in some cases even kerned correctly. Why is this? Is there a setting in LibreOffice I need to fiddle around with or do I need to adjust my font rendering in Ubuntu? I'd rather not learn LaTeX at this point in time ;)

Screenshot is from a .pdf of the document in question outputted by LibreOffice.

---

### Post by Ambimom on 2012-06-20
Beauty is in the eye of the beholder but .....

You might try:
Tools/Option/Fonts ...

then remove the checkmark next to 'non-proportional fonts only' if that is checked.

Also, I have a preference for serif fonts, so instead of choosing "Automatic," I'd choose Times New Roman or Liberation Serif.

Another thing I've noticed about LibreOffice is that if you're making many copy edits throughout a document, you have to scroll through the pages to fully align the text to the page.  Place the cursor a line or two above the edit and just move the scroll bar down to align  the newer  text to the existing page.    Sometimes, especially after adding chunks of new text to an existing document, the "fixes" are not really fully aligned to the rest of the text until the pages are scrolled.

---

### Post by Simian Man on 2012-06-20
I don't know if there is an answer.  I've *never* seen an office suite output documents comparable to what I produce in LaTeX.  That's what keeps me using it despite the headaches it causes now and then.

---

### Post by vasa1 on 2012-06-20
My suggestion is **not** to switch horses when you have important tasks at hand. Obviously, you're comparing the ugliness of LibreOffice to something else you were using. Just use that instead. There have been horror stories over at the OpenOffice.org forum about how software updates trashed dissertations or other important things. (Please don't ask why there were no backups).
The [latest]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=54584&sid=1b23571cb2f753960e56d123b21db2a9") is from someone who updated to Apache OpenOffice 3.4. Now her boss can't co-edit the dissertation.

---

### Post by Ambimom on 2012-06-20
From what I note on the LaTex site,

1.  They use proportional fonts
2.  They _**don't**_ use justification
3.  They use serif fonts

My own master's thesis (1993) typed with  $350 word-processing software, was done on a dot-matrix printer (with some $100 software addition that simulated normal printing).  It took 3 days (no lie) for the thing to print (running 24 hours a day).  It took me 4 more hours to pull off the paper sprockets and collate the thing.

Consider yourself lucky :lolflag:

Libre Office is an excellent package.

---

### Post by GreatDanton on 2012-06-20
Which font are you using, since I noticed if I type in Calibri then it's not smooth? But other fonts (which comes preinstalled) are beautiful and clear.

Maybe it's not problem with Libre office, but with the printer. Do you try printing your texts with your home printer or with proffesional one?

P.S 
Just to let you know. When I tried to open 50 pages in doc.x it opened. But when I tried 100 pages in doc.x Libre office collapsed. I don't know if this is also problem with odt format, but maybe you will have to split your text in 2 parts.

EDIT: I missed your question. If you are importing texts in PDF, the text will not be so clear as in Libre office/ my experience :). Why is so? Anyway try to print with pdf reader and see if there is a difference between pdf printing and Libre office printing.

Hope this helps

---

### Post by flemur13013 on 2012-06-20
Fonts were bad news under Unix, and they're still bad under Linux.

I've found that **changing the font** makes a big difference in kerning and overall quality/appearance. Although none seem to render as well as on MS systems, the "ubuntu" font renders especially poorly, and it might be your default font. (I removed it so it can't get used by accident).

---

### Post by yairsuari on 2012-06-20
did you  ever print it to paper?
the screenshot is not a good indication for printed output

---

### Post by ubiquitin.jf on 2012-06-20
I'm using Arial 11 pt, which is what my faculty requires all submitted work to be written in. What I'm comparing it to is .pdfs of papers published in journals like *J Virol* and *Nature*, who I should imagine use software costing thousands to get everything looking "just so". I'll print out a test page to see how it looks on paper; it might just look bad on an LCD.

---

### Post by kurt18947 on 2012-06-20
> **vasa1 said:**
> My suggestion is **not** to switch horses when you have important tasks at hand. Obviously, you're comparing the ugliness of LibreOffice to something else you were using. Just use that instead. There have been horror stories over at the OpenOffice.org forum about how software updates trashed dissertations or other important things. (Please don't ask why there were no backups).
The [latest]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=54584&sid=1b23571cb2f753960e56d123b21db2a9") is from someone who updated to Apache OpenOffice 3.4. Now her boss can't co-edit the dissertation.

That's what got my attention.  There were a few reports of theses going "poof" when they were just about finished.  The problems seemed to occur on systems with ext4 file systems.  I'd be sure to back up frequently to a separate partition or external drive or USB key.  There have been updates to Libre Office since this problem showed up, perhaps it's fixed.

---

### Post by jejones3141 on 2012-06-21
I think it's something about how LibreOffice renders the page on the display. I have a document that I've been editing in LibreOffice, and on the screen it looks like used cattle feed warmed over: horrible kerning, uneven color. If I print the document, the hard copy looks great. If I export the document to PDF and view the PDF, it looks great.

Either LibreOffice desperately needs to learn from the folks who wrote evince, or whatever library they use to display text on the screen is broken in some way.

UPDATE: This may be a known bug, i.e. {Open,Libre}Office not paying attention to GPOS kerning data.

---

