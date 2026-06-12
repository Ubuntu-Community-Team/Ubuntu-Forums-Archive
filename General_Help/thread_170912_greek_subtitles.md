---
title: "greek subtitles"
date: 2006-05-05
forum: General Help
---

### Post by vanalex on 2006-05-05
hello everybody! i've downloaded xine player and i can't see greek subtitles. has anyone got an idea how can i see them? thank you for reading my post and for your help...

vanalex

---

### Post by louis_nichols on 2006-05-05
I've set it in Totem with xine engine, so Xine itself shouldn't be very different.

In your home folder there should be a hiiden folder called ".xine" and in it a file called something like "xine_config" or "xine-config" or just "config" (you get the idea). Open this file for editing and find a section, usually commented out with #, that looks like:
```
# encoding of the subtitles
# string, default: iso-8859-1
subtitles.separate.src_encoding:iso-8859-2
```

Over there you should have iso-8859-7 which is for greek. Make sure that exact line doesn't have a # in front of it, too!

---

### Post by vanalex on 2006-05-06
I did what you told me but unfortunately xine can't keep the settings. i gedited the config file like this :

# encoding of the subtitles
# string, default: iso-8859-1
 subtitles.separate.src_encoding:iso-8859-7

but whenever i start the movie the config file comes back to its original form like this:

# encoding of the subtitles
# string, default: iso-8859-1
#subtitles.separate.src_encoding:iso-8859-1

If you had an idea i would appreciate it..Thank you..

---

### Post by louis_nichols on 2006-05-06
That is indeed strange. Try simply making the file non writable after changing it. It's a trick, but might just work.

---

### Post by spyrakos on 2006-08-01
I had the same problem, couldn't manage to solve it: either I saw a bunch of "########" (encoding=utf-8), or nothing at all except for punctuation symbols (?.;! etc.).

I resolved drastically using VLC, now everything works fine.;-)

---

