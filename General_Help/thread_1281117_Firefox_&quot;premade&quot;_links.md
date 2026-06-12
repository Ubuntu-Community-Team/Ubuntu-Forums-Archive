---
title: "Firefox &quot;premade&quot; links"
date: 2009-10-02
forum: General Help
---

### Post by Muscovy on 2009-10-02
You know those bookmarks that come with a fresh Firefox? Debian, Ubuntu help, FSF, etc? I'm trying to add to the bookmarks.html file, but I don't know how to do an icon. It seems to be ACSI or something. Could someone explain it?

---

### Post by dcstar on 2009-10-02
> **Muscovy said:**
> You know those bookmarks that come with a fresh Firefox? Debian, Ubuntu help, FSF, etc? I'm trying to add to the bookmarks.html file, but I don't know how to do an icon. It seems to be ACSI or something. Could someone explain it?

FF now uses an internal database for Bookmarks, not the old .html file.

---

### Post by Vaphell on 2009-10-02
[http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/d513c5fad30e64e3](http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/d513c5fad30e64e3)

---

### Post by akakingess on 2009-10-02
> **dcstar said:**
> FF now uses an internal database for Bookmarks, not the old .html file.

I do believe if you go into "organize bookmarks", that you can select folders and export as an .html file. As far as the icons go, I am afraid that I am not understanding what exactly you're looking to do.

---

### Post by Muscovy on 2009-10-02
The file I'm refering to is /etc/firefox-3.0/profile/bookmarks.html. It gives you some links to Ubuntu/Firefox content. Take a look at the file. You'll see huge streams on nonsense text in the image=. I want to know how to generate that text.


Edit: It's a base64 string. You run an image through a [compiler]("http://www.motobit.com/util/base64-decoder-encoder.asp") to get it.

---

### Post by akakingess on 2009-10-03
Wow, I hadn't ever noticed that before, but am even more stumped than before, I would say that they were links to the png images, but that is not even close to the case. I don't believe it is ASCII at all either, I would try some googling to see if it came up with something, ASCII art is way different and wouldn't created a png image (at least not to my limited knowledge).

---

