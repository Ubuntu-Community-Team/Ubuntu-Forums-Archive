---
title: "LottaNZB constantly shutdown unexpected"
date: 2011-06-22
forum: General Help
---

### Post by thunderbirdje on 2011-06-22
Hello everyone,

I've noticed that LottaNZB 0.6 always shutdowns after a certain amount of time (even when the NZB is not downloaded for 100%). This is kind of annoying because I can't rely on it to download files during the night.

I've run lottanzb --debug to get more information and this is the message which appears just before it shuts down. Hope anyone can help?

```
Pango:ERROR:/build/buildd/pango1.0-1.28.4/./pango/pango-layout.c:3819:pango_layout_check_lines: assertion failed: (end <= (layout->text + layout->length))
Aborted

```

I have no idea what Pango is and it seems that Google couldn't make me wiser this time :(

---

### Post by deviouskoopa on 2011-07-01
Nearly the same problem... wxPython GUI randomly shuts down after 1-3 minutes:

```
Pango:ERROR:/build/buildd/pango1.0-1.28.0/pango/pango-layout.c:3739:pango_layout_check_lines: assertion failed: (!layout->log_attrs)
Aborted
```

---

### Post by thunderbirdje on 2011-07-01
Hope someone can help us deviouskoopa and good to know we are with two now ;)

---

