---
title: "printing long lines across several pages"
date: 2012-06-22
forum: General Help
---

### Post by manthony121 on 2012-06-22
I am working with some MySQL databases, and often need to print out a table that is over 200 characters wide.  I can view the table onscreen using "less -S", but for a printed copy, even with my printer set to landscape, 17 cpi, the lines are too long to fit.  Is there a utility that will automatically cut the line at the right hand margin, and continue it on the next page?

I can do that by hand with something like, "cat sqltable.txt|cut -c -170|lp -dlp0 -ocpi=17 -olandscape; cat sqltable.txt|cut -c 171-340|lp -dlp0 -ocpi=17 -olandscape".

It wouldn't be terribly hard to wrap that into a script, but is there an existing utility that already does that?

---

