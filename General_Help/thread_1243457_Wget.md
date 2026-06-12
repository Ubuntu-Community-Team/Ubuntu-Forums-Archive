---
title: "Wget"
date: 2009-08-18
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-18
What's Up?

OK, So with my latest project finished, I then started to tweak some bits and bobs, One of my major speed and efficiency holes is one of the stages my script goes through is opening quite allot of links to web pages, Which firefox can withstand but it takes awhile to load.  So in order to quick the process up, I need to know if their is a way either via wget or another command line program is able to load the given page's and only _if_ the page is in .txt then save it to a file, if its html then do not save it.

Although the links end in .txt when they get opened up they mey be wrong and get the 404 error. But if they do work they would open in .txt.

Anyone Know A Way?

Thanks Bye.

---

### Post by DaithiF on 2009-08-18
wget in a loop should do just fine.

where does the list of links come from -- can't you filter out first the ones you don't want to just leave the .txt ones?

---

