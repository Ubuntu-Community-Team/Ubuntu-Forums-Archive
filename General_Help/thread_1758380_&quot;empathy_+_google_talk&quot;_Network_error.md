---
title: "&quot;empathy + google talk&quot; Network error"
date: 2011-05-14
forum: General Help
---

### Post by luvshines on 2011-05-14
After upgrade from 10.10 to 11.04, my gtalk account has stopped working in empathy

I am always hit with 'network error' message whenever I try to enable gtalk account.

My telepathy-gable package was missing after upgrade.
After installing it I observed a strange phenomenon - If I start empathy and then start /usr/lib/telepathy/telepathy-gabble manually from a terminal, empathy is able to connect to gtalk. It remains connected as long as that terminal remains open

Looks like empathy is not able to deploy telepathy-gabble on its own 

Some background in brief:-
I was first hit with the issue I reported here:
[http://ubuntuforums.org/showthread.php?t=1746755]("http://ubuntuforums.org/showthread.php?t=1746755")but it was resolved eventually

Then I was bumped with the current issue of 'network error'

Came across this thread but did not help
[http://ubuntuforums.org/showthread.php?t=1311005]("http://ubuntuforums.org/showthread.php?t=1311005")

Any help/suggestions guyz ??

---

### Post by debd on 2011-05-14
did you try running telepathy-gabble in the background with a '&'  ?

---

### Post by Durden on 2011-05-14
I would remove empathy and everything with it. Remove all the empathy config files in your user directory, then reinstall empathy fresh and rebuild the config.

Or just do what i did and switch to Pidgin. I hate empathy.

---

### Post by luvshines on 2011-05-14
> **debd said:**
> did you try running telepathy-gabble in the background with a '&'  ?

telepathy-gabble won't run without empathy running. It timesout and exits if it won't find connections```
/usr/lib/telepathy/telepathy-gabble
(telepathy-gabble:12337): tp-glib-DEBUG: started version 0.11.10 (telepathy-glib version 0.14.3)
(telepathy-gabble:12337): tp-glib-DEBUG: no connections, and timed out
tp-glib-Message: Exiting
```

---

### Post by luvshines on 2011-05-14
> **Durden said:**
> I would remove empathy and everything with it. Remove all the empathy config files in your user directory, then reinstall empathy fresh and rebuild the config.

Or just do what i did and switch to Pidgin. I hate empathy.

If I install pidgin, will it integrate into the 'chat accounts' section (top right corner on the panel, next to shutdown options) ?

---

### Post by Durden on 2011-05-14
I believe so yes.

---

### Post by luvshines on 2011-05-14
Well I have installed pidgin and it appears not under "chat accounts" but under "mailing" options as 'pidgin instant messenger' - I can live with that :)

But what bothers me most about pidgin is that if I wish to save passwords for my accounts, they are stored in clear text.

Since my system is shared by my friends too under a single username, that is a big issue for me and I can't live with that for sure

PS: Google chrome too saves it unencrypted :(

---

