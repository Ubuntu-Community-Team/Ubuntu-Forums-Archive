---
title: "Ubuntu 11.04 WebCam"
date: 2011-08-20
forum: General Help
---

### Post by FormatSeize on 2011-08-20
I don't know how to get this webcam thingy to work. I am using Ubuntu 11.04, and I have a HP Pro Webcam. I've never tried to use a webcam, and I'm at a loss right now. 

Any help is greatly appreciated.

---

### Post by mikewhatever on 2011-08-20
You need a program that makes use of webcams. What happens when you try launching Cheese?

---

### Post by FormatSeize on 2011-08-21
It works when I launch Cheese. But how do I use it with, say, Yahoo Messenger?

---

### Post by mikewhatever on 2011-08-21
I've never ever used Yahoo Messenger. Hope someone else can help you with that.

---

### Post by realzippy on 2011-08-21
..google for "Gyachi"

---

### Post by no2498 on 2011-08-21
you will need to install adobe flash
then in its settings manager you need to set the sites you use to allow and remember

---

### Post by FormatSeize on 2011-08-21
> **realzippy said:**
> ..google for "Gyachi"

I did. It got pretty late on me last night, and I was pretty lost when it came to installing it. I will install it and try it out in a few minutes and report back. 

Thanks.

---

### Post by FormatSeize on 2011-08-21
Now I'm trying to install gyachi. I've searched and searched and installed all sorts of stuff that it is asking for, but now it's asking for "gpgme.h". The output is as follows:
```
configure: error: cannot find include file gpgme.h. Perhaps you need to install the gpgme development package?
```

I have tried everything that I can think of, but I can't find what this stupid program is asking for. 

Any help is greatly appreciated.

---

### Post by FormatSeize on 2011-08-21
This is absolutely horrifying. 

I'm no expert, but I'm pretty good with computers and stuff. I have never had so much trouble with anything ever. I have installed gyachi, pidgin, and every other thing that could be imagined by the human mind. Yet, nothing will connect to Yahoo messenger. I've Googled, Binged, and even used Yahoo search, but I get nothing. 


Perhaps I'm an idiot, I don't know. I just want this to work.

---

### Post by realzippy on 2011-08-21
Why did you compile?

```
sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi
```

from
[http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html](http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html)

---

