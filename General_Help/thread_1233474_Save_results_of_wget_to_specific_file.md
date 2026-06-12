---
title: "Save results of wget to specific file?"
date: 2009-08-06
forum: General Help
---

### Post by josephellengar on 2009-08-06
I'm trying to get my conky to show my public IP address.  I found this site: [http://www.showmyip.com/simple/](http://www.showmyip.com/simple/) which shows my ip address very simply, but I can't figure out how to get wget to save the information there to a specific file.  It keeps saving it to index.html.  Is there any way to get it to save the information to a file like .myip or something?  Thanks.

---

### Post by martinbaselier on 2009-08-06
If you just want to download one file, you can use -O file.
Use **man wget** for more information. 
in man type / to search:
/-O
will bring you to the correct section immediately.

---

### Post by josephellengar on 2009-08-08
> **martinbaselier said:**
> If you just want to download one file, you can use -O file.
Use **man wget** for more information. 
in man type / to search:
/-O
will bring you to the correct section immediately.

That's the log.  I'm trying to just get the entire page, without any log or time left.  It should be a single line text file, using the URL that I gave before.

---

### Post by andrew.46 on 2009-08-09
Hi idigchess,

> **idigchess said:**
> That's the log.  I'm trying to just get the entire page, without any log or time left.  It should be a single line text file, using the URL that I gave before.

I think you might have confused -O with -o, the first allows you to specify the output file for wget while the second allows you to specify the logfile. So I guess you are after:

```
wget http://www.showmyip.com/simple/ -O file
```

Hopefully this is what you are after?

Andrew

---

