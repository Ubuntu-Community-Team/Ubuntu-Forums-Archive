---
title: "Problem with printer banner"
date: 2011-02-23
forum: General Help
---

### Post by FuzZy2006 on 2011-02-23
I have a Xerox WorkCentre 5222 without PostScript. I have added it in cups using the ppd provided in the manufacturer's cd. The problem is that the file contains some postscript filter statements. I have removed those but it did not print. 

I have then installed instead using the c2424 foomatic jpks pcl5c driver from the list from cups. It prints without problem. The only thing is that I can't get rid of the banner page. I have disabled that from lpadmin, from cups, but it doesn't work. I have searched for the banners folder, found it, and removed the files. It still prints the same banner. I have also modified them, but the modifications don't change the banner. 

Do you know which other config file may be related to the banners or what else I can do?

Thank you.

---

### Post by gmargo on 2011-02-23
The cups parameter controlling banner pages is "JobSheets" in the printers.conf file.  For each of the configured printers in my printers.conf there is an entry:
```

JobSheets none none

```Do you have that entry?

Update: The "JobSheets" parameter can also appear in the classes.conf file.

---

