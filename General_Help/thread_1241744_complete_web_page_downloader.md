---
title: "complete web page downloader"
date: 2009-08-16
forum: General Help
---

### Post by rastro123 on 2009-08-16
Hi, is there a webpage downloader I can install to download the whole website? Whats the command pls? Many thanks.

---

### Post by wojox on 2009-08-16
Put that in your terminal:
```
man wget
```

---

### Post by rastro123 on 2009-08-16
thanks mate, and I take it, man wget and the url of the website?

---

### Post by rastro123 on 2009-08-16
oh yes, I see now. thanks a lot

---

### Post by rastro123 on 2009-08-16
I got it downloading a site now- where does it download to mate? How do I find it? Many thanks.

---

### Post by Finalfantasykid on 2009-08-16
I think it just downloads to your current working directory(type ls after wget is done).

And I didn't know wget can be used to download an entire website.  Are you using an ftp as the url?

EDIT:  Oh cool, you can download the entire site...
```
wget -r --password=yourPassword ftp://yourUserName@yourDomain.net

```

And I also checked, it it does download to your current working directory, so you might want to mkdir a directory for what you are storing before hand.

---

### Post by Keith Hedger on 2009-08-16
Try WebHTTrack its in the repos and works well.

---

