---
title: "easily viewing documentation"
date: 2010-08-07
forum: General Help
---

### Post by youbantwo on 2010-08-07
I just downloaded libgtk2.0-doc at the gtkmm docs to help me with some programming. I've found where the libgtk2.0 documents are (/usr/share/gtk-doc/html) and I'm not for sure where the gtkmm docs are.

My question is: what is an easy way to view all of these HTML files? I know on Ruby you can run gem-server and you can see all of your RDocs from localhost on your browser. Is there an equivalent to that on Ubuntu for gtk-doc?

---

### Post by darolu on 2010-08-07
I usually just open them in a browser window (firefox or chromium), the ones I've read have navigation arrows and a nice index.

Edit: I just installed libgtk-doc and it looks exactly the same as the others I've read. You shouldn't have any problem.

[IMG]http://i34.tinypic.com/2vam3k7.png[/IMG]

---

### Post by youbantwo on 2010-08-07
thanks for showing me that, I was wondering if there was like a stream-lined way of doing this so you don't have to search around docs you've just installed and type in long URLs into firefox. I wonder if this would be a worthwhile coding endeavor...

---

### Post by darolu on 2010-08-07
Well you can also use devhelp:
```
sudo apt-get install devhelp
```

---

### Post by youbantwo on 2010-08-08
> **darolu said:**
> Well you can also use devhelp:
```
sudo apt-get install devhelp
```
crap, I spent all night on this stupid python script that used python-apt to search for documentation and where it was installed on a user's computer.

thanks for showing me that though

---

