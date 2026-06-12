---
title: "Opening a browser in WINE."
date: 2010-10-26
forum: General Help
---

### Post by ki4jgt on 2010-10-26
I have been working on this program for Windows all month [http://www.smashindex.com](http://www.smashindex.com) it is a logging program for amateur radio. Anyway, 75 percent of my users are using Linux. I'm guessing with WINE because the program is Windows based. That's all fine and well with me, but I have a problem. The donations option, opens a browser and lets the user make a donation to my paypal account, and the callsign lookup option opens the browser to the qrz.com database for whatever callsign the user enters. WINE, doesn't seem to support opening browsers for my software, but I've seen it do it for other software. I was wondering what I needed to run to have WINE open a browser on linux like the other software I've seen do it.

Here is a snippet of the code used to open the browser to my donations page:

```
        [DONATE]

            CLS

            PRINT "SMASHINDEX.COM WOULD LIKE TO THANK YOU FOR DONATING"

            PRINT "TO THE DEVELOPEMENT OF THIS AND OTHER SMASHINDEX"

            PRINT "OPEN SOURCE FREEWARE."

            PRINT

            INPUT "PLEASE PRESS 'ENTER' TO BE TAKEN TO OUR DONATION PAGE"; ENT

            LET ADDRESS$ = "https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=TEFFKQF83EBJ4"

            RUN "rundll32.exe url.dll,FileProtocolHandler ";ADDRESS$ 

            GOTO [BLANK]
```

What can I run the URL with that WINE will understand?

---

### Post by ki4jgt on 2010-10-26
No views, no replies??? what in the world?

---

### Post by Mark Phelps on 2010-10-26
Before you start complaining, you should first post your question in the CORRECT forum. This forum is General Help.  Had you taken a couple of minutes to look around, you would have found the Wine subforum -- under Other Community Discussions.  You would have received better support had you posted it there.

Also, according to the time-frame, you posted your complaint less than one hour after your original post.  You think we're all sitting here just waiting for you to post?

Have some patience -- and post to the right place.

---

### Post by ki4jgt on 2010-10-26
LOL :-) sorry, it's just usually I get faster responses or at least about 16 views in about 5 minutes. When I posted that. I didn't even have 1 view. O well, and I wasn't complaining, just using really bad sarcasm.

---

