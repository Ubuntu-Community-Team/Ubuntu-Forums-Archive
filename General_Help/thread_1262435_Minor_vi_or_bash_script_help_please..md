---
title: "Minor vi or bash script help please."
date: 2009-09-09
forum: General Help
---

### Post by galoluscus on 2009-09-09
Hey, thanks for reading and possibly helping.
 
  here is my delima:
  I am creating a list, from scratch, using vi on Ubuntu Hardy.
The format of which is:
Brand           Size         Type             Serial
Ansul            20            abc              xa220433
Ansul Sentry 2.5           abc              zf-1103
simplex        20                               203877
 
  The problem is, now that I have entered about 250 lines, I realize I should have used 
CApitol letters in the serial numbers.  I have been diging through my 'script file' and nothing seems to operate the way I want it to.  I know this is a simple thing, in both vi or a bash script, but could use some help - in either.
-  Not all serials have dashes or letters. 
  This is what I get for volenteering my time for work. (they use windoze :-( )
 
  Anyway, I greatly appreciate any help with this.
 
 
   Thank You and Good Day.
  .jason

---

### Post by yabbadabbadont on 2009-09-09
Are the columns spaced such that they line up vertically?  (if so, vim in visual selection mode is an easy fix)
Are there always four fields on each line?  (your last example line only has three...)
Are there any embedded spaces within a field?  (looks like there are from your second example line)

---

### Post by galoluscus on 2009-09-09
Yea, there are 4 colums for some, but not all, and yes, they line up vertically.
 I left the 'space' blank where there is no data for those spaces. All colums are seperated by tabs, these are consistant "down" the file, but not across a line:  
ie:  data - 2 tabs; data - 3 tabs; data - 3 tabs. 
 Again thank you. I will check Visual Selectio Mode.

---

