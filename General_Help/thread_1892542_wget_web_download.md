---
title: "wget web download"
date: 2011-12-08
forum: General Help
---

### Post by cortman on 2011-12-08
I understand it's possible to download an entire website (complete with linked pages, etc.) for offline viewing using wget and a few flags. I tried this and it did indeed download a lot of data, but all the pages are in .php format, which I have trouble viewing in a browser. How can I get it downloaded as .html?
Thanks!

---

### Post by ZenMasterInTraining on 2011-12-08
Hello Richard Stallman, still browsing the internet with Wget?

wget -r -p -e robots=off [http://www.example.com](http://www.example.com) 

Try this.

---

### Post by Habitual on 2011-12-08
> **ZenMasterInTraining said:**
> ...robots=off...

You have much to learn. Zen Masters don't bypass others security EVEN IF THEY CAN.

---

### Post by Lars Noodén on 2011-12-08
[font=Courier New]wget[/font] takes the filenames as the server gives them.  You could try re-writing the names with a shell script but that would break the links in your documents.  Your browser should be able to figure out the links regardless of what the pages are called.  Have you tried using the [font=Courier New]-k[/font] option?

---

### Post by cortman on 2011-12-08
> 
Hello Richard Stallman, still browsing the internet with Wget?

wget -r -p -e robots=off [http://www.example.com](http://www.example.com) 

Try this.

Browsing the web with wget? How passe. Try [elinks]("http://elinks.cz/").

@Lars- I tried -k but it didn't do it. I suppose it'd be easy enough to rename them all as .html, but like you said, the links would be broken, which would be a major pain.

---

