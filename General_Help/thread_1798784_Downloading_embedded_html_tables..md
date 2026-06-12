---
title: "Downloading embedded html tables."
date: 2011-07-06
forum: General Help
---

### Post by rogueit on 2011-07-06
I am looking for a scriptable solution for downloading tables that are embedded into webpages. If I wanted to save this table to a csv file what would I need to use. On Winders, I currently have Excel doing the job with a script. 
 
[http://www.barchart.com/stocks/high.php?_dtp1=0](http://www.barchart.com/stocks/high.php?_dtp1=0)
 
Any help or pointers would be greatly appreciated.
 
Thanks
RogueIT.

---

### Post by nzjethro on 2011-07-06
You can do this with LibreOffice (and probably OpenOffice too). Simply copy the html table, switch to a blank LibreOffice Calc document, then go Edit > Paste Special then select HTML rather than No Formatting. You can then save it as a csv to your needs.

Was this what were you wanting, or were you wanting a script to automate this process?

---

### Post by rogueit on 2011-07-06
I was going to run it from cron on a server so I don't have to worry about doing it everyday.  Right now I use a vb script for the whole batch from downloading, saving and importing into Access. 
I have to believe that if you can do it in Windows, you can do it in Linux. I just need someone to show me the door...I can walk through it.

---

