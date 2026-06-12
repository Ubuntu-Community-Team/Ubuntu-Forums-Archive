---
title: "Only one application connects to internet??!?"
date: 2009-12-30
forum: General Help
---

### Post by anaconda on 2009-12-30
I finally moved to 9.10, and now I have a strange problem.

I can connect to the internet, but it seems that only one program has the internet connection at one time.

eg. in one terminal i am installing programs using "apt-get install xxx" And it is downloading them at the full speed of my (slow) internet connection

Then I open another terminal and type:
```
ping www.google.com
```
and after couple of minutes ping returns: unknown host

The same thing if I open firefox and try to open any page.. No connection.

however after apt-get finishes downloading both ping and firefox work normally.

????????????????????????

---

### Post by pirlo89 on 2009-12-30
im new to ubuntu but this is what i have for you...

try to open firefox and any other browser at the same time . and then open with these browsers a light page like google. if they both work then you know that your problem is that when downloading at full speed, its not possible to open any other webpage.

note : that what happens between me and my brother, i download and he complains that the internet doesnt work:(

---

