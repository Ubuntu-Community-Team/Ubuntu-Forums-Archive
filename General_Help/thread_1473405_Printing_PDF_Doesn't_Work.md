---
title: "Printing PDF Doesn't Work?"
date: 2010-05-05
forum: General Help
---

### Post by moore.bryan on 2010-05-05
Can someone give me some direction in which to debug this:
When I try to print *any* PDF from either Acroread or Evince, it doesn't print and the queue tells me the printer isn't connected; and yet, when I print from OpenOffice.org, everything's fine.

Help?

---

### Post by sbergman on 2010-05-05
I had a similar strange problem about a week ago.... the jobs werent printed out and I received no error messages.

The workaround at the time was to open up a terminal, cd to the document I wanted to print (file.pdf) and then type the command
lpr ./file.pdf

It printed out the document to the default printer.

---

### Post by moore.bryan on 2010-05-06
Thanks for the hint... I'll try it. To just complicate things a bit, I apparently can only _not_ print multi-page PDF's; single-page PDF's print just fine.
Nice.

Edit:
No dice.
:-( !

---

### Post by moore.bryan on 2010-05-10
Anyone have any ideas how I can fix this?

---

