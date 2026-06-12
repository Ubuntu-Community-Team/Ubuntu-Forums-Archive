---
title: "streamtuner problems"
date: 2006-05-08
forum: General Help
---

### Post by Melciah on 2006-05-08
has anyone managed to get streamtuner installed on breezy?
i get this:
> 
 streamtuner depends on libtagc0 (>= 1.3.1); however:
  Package libtagc0 is not installed.
 streamtuner depends on python2.3 (>= 2.3); however:
  Package python2.3 is not installed.
 streamtuner depends on python (<< 2.4); however:
  Version of python on system is 2.4.2-0ubuntu2.

two things though. 
1. does this mean im forced to go back to an earlier version of python, and
2. i cant find libtagc0 in synaptec or on google.

---

### Post by Sef on 2006-05-08
Try this from the terminal:

sudo apt-get update

sudo apt-get install python2.3

then see if it will install.  If not then istall these two via sudo apt-get install package_name

```
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]

```

---

### Post by Melciah on 2006-05-08
hi. thanks for the reply. i retried using synaptec not five minutes ago. i was having problems with the repos. it worked fine this time. I didnt even think it was in the repos earlier. thanks

---

