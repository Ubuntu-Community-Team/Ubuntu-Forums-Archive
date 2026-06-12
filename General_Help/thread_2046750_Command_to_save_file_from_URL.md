---
title: "Command to save file from URL"
date: 2012-08-23
forum: General Help
---

### Post by ChemMeister on 2012-08-23
Hi,

I was wondering if there is a linux command to save a file from a URL when inside a terminal. So for example we have "http://www.myfiles.com/myFile.pdf", opening this link in a web browser will get prompted if you want to save the file. But is there a command to save "myFile.pdf" directly from the termninal. Thanks

---

### Post by Marqin on 2012-08-23
```
wget http://www.myfiles.com/myFile.pdf
```

---

### Post by Lars Noodén on 2012-08-23
wget is certainly the way to go.  Be sure to take a look at all the [options](http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html) that it gives you. They might come in handy sometime later.

---

### Post by Marqin on 2012-08-23
Yeah, pay attention to option "-c" ;)

---

### Post by cortman on 2012-08-23
There's also [cURL]("http://www.cs.sunysb.edu/documentation/curl/index.html"), although I usually use wget myself.

---

