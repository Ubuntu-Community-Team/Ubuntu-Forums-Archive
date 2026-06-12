---
title: "ecryptfs eats up a lot of space?"
date: 2010-06-28
forum: General Help
---

### Post by stoneweg on 2010-06-28
Hi!

In my home directory, when I type

```
du -hs
```

I get

```
215G    .
```

This is definetely too much, since when I do

```
du -hs *
```

I get

```
40M	Desktop
4.0K	Documents
251M	Downloads
102G	Dropbox
12K	examples.desktop
4.0K	Music
8.0K	Pictures
3.6M	Programme
4.0K	Public
2.1G	scm
4.0K	Templates
8.0K	Ubuntu One
4.0K	Videos
```,

which is approximately HALF the space than actually needed. Is this increase due to ecryptfs? Also I noticed that the hidden folders are not shown. Are the hidden files within the shown folders included in this list? How do I show a summary which includes the hidden files?

Thanks for any help!

---

### Post by stoneweg on 2010-06-28
Ok, I found the problem by myself: there was a hidden file called ".xsession-errors.old" in my home directory which was 108GB big!!!

Definetely I am surprised that such things still happen in Ubuntu... and now please don't tell me I should have looked into the file to see what kind of errors are reported. Such a file should NEVER EVER be allowed by default to grow so much!

---

