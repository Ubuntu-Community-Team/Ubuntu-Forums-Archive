---
title: "invest chart applet graphs"
date: 2011-02-25
forum: General Help
---

### Post by configt on 2011-02-25
If your invest applet stopped graphing (when you double click on the  stock item from inside the applet window), this solution might work.

On my 9.04, 9.10 and 10.04 installs, I was able to get the invest applet  to start graphing again by changing line 209 of this file:

/usr/share/pyshared/invest/chart.py

from:


chart_base_url =  "http://ichart.europe.yahoo.com/z?s=%(s)s&t=%(t)s&     q=%(q)s&l=%(l)s&z=%(z)s&p=%(p)s&a=%(a)s%(opt)s"

To:

chart_base_url = "http://ichart.yahoo.com/z?s=%(s)s&t=%(t)s&     q=%(q)s&l=%(l)s&z=%(z)s&p=%(p)s&a=%(a)s%(opt)s"

(notice 'europe' was removed from the URL).

Then simply remove the invest applet from your panel and then add it again.

I hope this helps someone.

:smile:

---

### Post by JBBVe on 2011-03-10
Many thanks for your help.
I was really missing the graphs.

Cheers

---

### Post by joelk on 2011-06-09
I also had been missing the charts or stock graphs. Thanks for the fix.

I had a difficult time searching for this solution.  Part of my problem was that I was searching on the error message "Chart could not be downloaded".  Maybe by including the text of the error in my post, I can help someone else find this thread more easily.

---

