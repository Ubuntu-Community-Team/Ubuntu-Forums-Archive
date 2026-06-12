---
title: "wget webpage and some links for offline view"
date: 2010-04-25
forum: General Help
---

### Post by waznot on 2010-04-25
I've looked around the other threads as well as the wget man page. I also Googled for some examples.  I still cannot work it out.


From the page 

[COLOR=RoyalBlue][http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=Hard-Drive&servicetag=BBWKG1S&SystemID=DIM_CEL_3000&hidos=WW1&hidlang=en&TabIndex=0&scanSupported=False&scanConsent=False](http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=Hard-Drive&servicetag=BBWKG1S&SystemID=DIM_CEL_3000&hidos=WW1&hidlang=en&TabIndex=0&scanSupported=False&scanConsent=False)[/COLOR]

I want to download the 48 linked files and their corresponding information page.[INDENT]To do this (the first file) by hand I click on the line that says[INDENT][SIZE=2][COLOR=DimGray]Applications (5)[/COLOR][/SIZE]
[/INDENT]Go to the first option[INDENT][SIZE=2][COLOR=Blue]Dell - Application[/COLOR][/SIZE]
[/INDENT]Open and copy the linked page[INDENT][SIZE=2]Applies to:
[/SIZE] [SIZE=2][COLOR=Blue]Driver Reset Tool[/COLOR][/SIZE]
[/INDENT]Then back on the first page click on the Download button.  On the window that opens up I choose to save the file.

Then I move on to the next option (which is Sonic Solutions - Applications) and repeat this until I would have all my files.
[/INDENT]I do not want to download the many other links on this page.  Just the above mentioned, so I can take it back to my internet-less place and refer to it as if I was on the net.

I am using the 9.10 LiveCD at my friends place.

---

### Post by blueridgedog on 2010-04-25
Since the pages are generated on the fly via aspx, I don't think wget will be able to work.  Each page exists only as a rendered output from a request for an aspx web page with arguments.  wget can guess at the arguments.

The only option appears to be to scrape the entire site ([http://widgetbuilding.com/archives/11-Howto-Scrape-an-ASP-site.html](http://widgetbuilding.com/archives/11-Howto-Scrape-an-ASP-site.html)) but that would be very large.

---

### Post by waznot on 2010-05-08
Thank you blueridgedog. I will look into your suggestion.

---

