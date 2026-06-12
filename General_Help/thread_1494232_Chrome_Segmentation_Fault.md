---
title: "Chrome Segmentation Fault"
date: 2010-05-26
forum: General Help
---

### Post by matshofman on 2010-05-26
When i startup Google Chrome it immediately closes.

When i use the google-chrome command in the terminal it gives this message

```
...:~$ google-chrome
Segmentationfault
...:~$ 
```I hope someone can help me

(i'm using 10.04)

---

### Post by bodhi.zazen on 2010-05-26
> **matshofman said:**
> When i startup Google Chrome it immediately closes.

When i use the google-chrome command in the terminal it gives this message

```
...:~$ google-chrome
Segmentationfault
...:~$ 
```I hope someone can help me

(i'm using 10.04)

You should probably ask on the google chrome mailing list / forums as chrome is a 3rd party application not maintained by the Ubuntu developers.

[http://www.google.com/support/forum/p/Chrome](http://www.google.com/support/forum/p/Chrome)

[http://www.google.com/support/forum/p/Chrome/label?lid=3534bfada77d07a9](http://www.google.com/support/forum/p/Chrome/label?lid=3534bfada77d07a9)

Alternately you can try chromium, it is in the lucid repositories

```
sudo apt-get install chromium-browser
```

---

### Post by matshofman on 2010-05-27
Thnx Chromium works for me!

---

### Post by bodhi.zazen on 2010-05-27
> **matshofman said:**
> Thnx Chromium works for me!

Fantastic.

Personally, IMO, Chromium is very close to replacing firefox, it has a few minor annoyances yet that slightly outweigh the annoyances of firefox at the moment, but Chromium is much improved over the last few months.

I hope the developers release an apparmor profile soon, I write my own.

While chromium may be sandboxed, not all of the extensions are, for example Flash is not sandboxed, and the technical details of the sandbox are a bit scanty.

---

### Post by velko on 2010-07-06
I had a similar problem in which google-chrome-unstable  began to emmit segmentation fault and die right after a package update...

I was **very scared** that I would lose all my settings / saved sessions / bookmarks etc...

The fix was to downgrade the package to the prev version.

To receive instructions about this - please find me on skype: velkoradulov or at vladimir .at. velko.org .

---

### Post by d2843 on 2010-12-20
I clicked this hoping for some real information for getting rid of the segfault. What am I supposed to do if both chrome and chromium are segfaulting?

---

### Post by bodhi.zazen on 2010-12-20
> **d2843 said:**
> I clicked this hoping for some real information for getting rid of the segfault. What am I supposed to do if both chrome and chromium are segfaulting?

File a bug report with google or the chromium project. Neither is maintained or coded here.

---

