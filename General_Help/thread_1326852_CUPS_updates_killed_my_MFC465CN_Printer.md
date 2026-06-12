---
title: "CUPS updates killed my MFC465CN Printer"
date: 2009-11-14
forum: General Help
---

### Post by jakev383 on 2009-11-14
I have a laptop running 8.04 that used to print just fine to my Broher MFC 465CN printer via the network. I remember cups updates a little while back and today when I tried to print (I don't print to this printer much) it would not print. After messing around with it for an hour or so, I decided to try and get it to print on my 9.04 amd64 desktop. Here is the error message I get on the 64-bit desktop:
```

E [14/Nov/2009:20:04:37 -0500] PID 5833 (/usr/lib/cups/filter/brlpdwrappermfc465cn) crashed on signal 9!
E [14/Nov/2009:20:04:37 -0500] PID 5838 (/usr/lib/cups/backend/socket) crashed on signal 9!

```

I followed this guide:
[http://ubuntuforums.org/showthread.php?t=590793&highlight=brother+mfc+465cn](http://ubuntuforums.org/showthread.php?t=590793&highlight=brother+mfc+465cn)
I then tried this one:
[http://ubuntuforums.org/showpost.php?p=3835451&postcount=61](http://ubuntuforums.org/showpost.php?p=3835451&postcount=61)

Still both with no go. The second one looks to have been more promising, with this error:
```

 [14/Nov/2009:20:10:19 -0500] cupsdAuthorize: Local authentication certificate not found!
E [14/Nov/2009:20:10:19 -0500] cupsdAuthorize: Local authentication certificate not found!
E [14/Nov/2009:20:10:19 -0500] cupsdAuthorize: Local authentication certificate not found!
E [14/Nov/2009:20:10:19 -0500] cupsdAuthorize: Local authentication certificate not found!

```

On my laptop, after following the first link, I get this error:
```

E [14/Nov/2009:19:47:30 -0500] [Job 81] No %%BoundingBox: comment in header!

```

Why do updates always break crap?
Any suggestions are appreciated.

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
[http://ubuntuforums.org/showthread.php?t=571621](http://ubuntuforums.org/showthread.php?t=571621) looks like it helped some. Sorry if you already tried.

---

