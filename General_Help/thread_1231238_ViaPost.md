---
title: "ViaPost"
date: 2009-08-04
forum: General Help
---

### Post by kdavies on 2009-08-04
Has any one got ViaPost working with Ubuntu?

Its a great app that allows you do print and post from the pc.

They have also got open api for those who can program.

[http://www.viapost.com](http://www.viapost.com)

---

### Post by Printing&amp;Postage on 2009-08-04
Your probably better off using a wrapper for their API, rather than porting the driver.

I'm with [Docmail ]("http://www.cfhdocmail.com")(a ViaPost competitor).  We both have SOAP-based API's available to be completely platform independent.

It would be great to see some [Hybrid Mail]("http://en.wikipedia.org/wiki/Hybrid_mail") stuff coming out of the Open source community.

Basically, with either Docmail or ViaPost, you can write a wrapper app to submit Word files (Docmail only)/PDF's with address(es) and mail-merge data (Docmail only) & the services address/mail-merge the documents, print them, and send them out in the post.

Ours API's better though :)

Cheers.
Will

API links:
[http://www.programmableweb.com/api/docmail](http://www.programmableweb.com/api/docmail)
[http://www.programmableweb.com/api/viapost](http://www.programmableweb.com/api/viapost)

---

