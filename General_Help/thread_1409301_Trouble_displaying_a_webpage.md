---
title: "Trouble displaying a webpage"
date: 2010-02-17
forum: General Help
---

### Post by jwbrase on 2010-02-17
I'm not sure if the counts for "general help" since it's likely a problem on the server end, but there is a chance it's on my end, and even with a problem on the server end I figure there may be some potential fix on my end.

First of all, please follow this link and state whether the page loads or not. If it loads for anybody else, it might be a problem on my end.

[http://isthe.com/chongo/tech/astro/HR-temp-mass-table-byhrclass.html](http://isthe.com/chongo/tech/astro/HR-temp-mass-table-byhrclass.html)

Opera and Firefox both just display a blank page, and curl gives:

```
curl: (18) transfer closed with 391975 bytes remaining to read
```

I had loaded this page in the past, and the rest of the site seems to still be up. Also, the server appears to have the file and be transmitting how big it is, but then giving up mid-transmission, or that's what it seems like from the message that curl gives.

Any ideas?

---

### Post by Jackzor on 2010-02-17
Its a blank page for me. I even tried to View Source and it comes up blank.

---

### Post by steveneddy on 2010-02-17
Maybe that particular web page you are trying to view is not up at the moment.

The main page loads fine, so it looks like the server is working.

---

### Post by houseworkshy on 2010-02-17
Yes the site is up according to [http://downforeveryoneorjustme.com](http://downforeveryoneorjustme.com) and the page is blank.  Don't know what to do about it but the problem is not at your end.

---

### Post by jwbrase on 2010-02-17
> **steveneddy said:**
> The main page loads fine, so it looks like the server is working.

Which is also indicated by the fact that curl gives the size of the file it was expecting and didn't get. That would indicate that the server is up, the file is on the server, and a transfer is starting, but something is interrupting the transfer.

---

