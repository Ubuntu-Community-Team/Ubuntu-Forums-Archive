---
title: "Stock Market EOD Quote Retriever"
date: 2010-02-22
forum: General Help
---

### Post by BambooClaw on 2010-02-22
Anyone know of of an automated stock market end of day quote retriever?
Ideally this software would be a service that automatically updated a MySQL Database of stock quotes for EOD data (probably from Yahoo).

Any help appreciated.

---

### Post by preumbra on 2010-02-27
I have seen to reasonably priced options:

1) Below is a link that allows you to use matlab data for a single ticker.  I suppose you can automate that in matlab.  You could easily write a routine to get all the symbols you want.

[http://luminouslogic.com/how-to-download-historical-stock-data-into-matlab.htm]("http://luminouslogic.com/how-to-download-historical-stock-data-into-matlab.htm")

2) Also I saw a download from [http://www.eoddata.com/](http://www.eoddata.com/) (its about $25 for NYSE).  It is not free but not too bad, and that could easily be put into a data base.

Let me know what you find out, I want to do this myself - but won't get to it for a few weeks probably.

---

### Post by yccheok on 2010-03-02
Not sure whether this will meet your requirement :

[http://jstock.sourceforge.net]("http://jstock.sourceforge.net")

Is a full feature stock market software, which grabs data from Yahoo Finance. If it doesn't meet your requirement, perhaps you may modify its feed engine source code (Is open source and written in Java)

---

