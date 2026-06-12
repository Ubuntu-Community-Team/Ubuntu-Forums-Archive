---
title: "Corrupt pdf printing"
date: 2012-10-09
forum: General Help
---

### Post by iaw4 on 2012-10-09
I am running ubuntu 12.04.1 .  I have multiple printers: a local Lexmark C544 and a remote Ricoh Aficio MP-9000.  (the latter is a high-speed copier and printer that can run through a ream of paper in a minute, but it is a few rooms away.)

I believe cups is sending jobs in raw pdf to my printers.  I believe neither of my printers is smart enough to understand pdf.  they understand ps, but not pdf.  on the Ricoh, I have thus printed hundreds of white pages, some with scribbles at the top.  the first page contains some text with a Glyph & Cog copyright notice, a line-feed, then /xpdf and more stuff.

if I hand-convert my pdf files to postscript files, I can print the postscript file just fine.

My problem happens when I try to print from a variety of applications, such as from okular.  I also have the impression that my problem is more likely to arise if I have a job-special, such as a request to print double-sided or only the first page.  However, I am reluctant to experiment with it---the Ricoh will print a few hundred pages before I can convince it to stop.  the Lexmark is usually smart enough to just stop after one page (or it suppresses the job altogether).

Are the ubuntu 12.04 pdf print drivers broken?  Even though OSX uses the same underlying cups daemon, it never exhibited such symptoms.

what's going on here?

regards,

/iaw

---

