---
title: "SQLite"
date: 2009-12-18
forum: General Help
---

### Post by jerrrys on 2009-12-18
I want to switch from FF to Chrome.  Problem is I use [Zotero ]("http://www.zotero.org/")which is not supported by Chrome.  Zotero is based on SQLite.  Question would be if I would be better off just going to SQLite?

---

### Post by bodhi.zazen on 2009-12-18
sounds like it =)

---

### Post by lovinglinux on 2009-12-18
I don't see how that would help. Would be better if you contact Zotero developers and ask for a Chrome extension.

Keep in mind that porting an extension might not be easy or feasible. I have been wondering about porting my extensions, but I have already enough work to do on the original versions, which also relies on SQLite. I don't know how Chrome stores data, but if it doesn't use SQLite, then I will probably not even start. 

Chrome is cool and extremely fast, but let's face it...it can't beat Firefox in terms of customization and extension availability.

If you are switching because of performance, see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by jerrrys on 2009-12-18
hi lovinglinux

i am a supporter of your thread and have UMarks

as for FF, im one of the lucky ones, its been fast from install (3.0)

as for SQLite, just looking for opinions, i will probably load it to play with for now

---

### Post by lovinglinux on 2009-12-18
> **jerrrys said:**
> hi lovinglinux

i am a supporter of your thread and have UMarks

as for FF, im one of the lucky ones, its been fast from install (3.0)

as for SQLite, just looking for opinions, i will probably load it to play with for now

Hey, thanks. Have you downloaded the latest version of Umarks? I have uploaded it last week. There is a bug when combined with All-in-One sidebar, but other than that is a very nice version. The interface is much simpler now and it doesn't require sqlite3 anymore.

> **jerrrys said:**
> as for SQLite, just looking for opinions, i will probably load it to play with for now

Check [SQLite Manager extension](https://addons.mozilla.org/en-US/firefox/addon/5817) for Firefox. It is a very nice tool if you want program using SQLIte and for managing existing databases.

---

### Post by jerrrys on 2009-12-18
quote:  Check [SQLite Manager extension]("https://addons.mozilla.org/en-US/firefox/addon/5817") for Firefox. It is a very nice tool if you want program using SQLIte and for managing existing databases.

that would still tie me to FF and if i recall right FF notified me of your update, but i have not installed it yet...have to get on that, its a great information resourse.

---

### Post by lovinglinux on 2009-12-18
> **jerrrys said:**
> that would still tie me to FF ...

Then install [sqlitebrowser](apt:sqlitebrowser).

> **jerrrys said:**
> ...and if i recall right FF notified me of your update, but i have not installed it yet...have to get on that, its a great information resourse.

I don't think so, since it is an experimental add-on. As far as I am aware, experimental add-ons don't have automatic update functionality. You have to manually check and download them from Mozilla's web site.

---

### Post by jerrrys on 2009-12-18
your link is not working, but yes, its light duty and may be what im looking for...thanks

---

### Post by lovinglinux on 2009-12-18
> **jerrrys said:**
> your link is not working, but yes, its light duty and may be what im looking for...thanks

Then

```
sudo apt-get install sqlitebrowser
```

---

### Post by jerrrys on 2009-12-18
thanks again and on a side note, im on Win7 right now and FF is only slightly faster than my ubuntu, go figure...

---

### Post by jerrrys on 2009-12-19
well another day...

dont like the user interface on sqlite browser.  zotero really got me spoiled, the search goes on...

---

