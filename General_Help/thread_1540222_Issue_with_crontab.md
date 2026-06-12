---
title: "Issue with crontab"
date: 2010-07-27
forum: General Help
---

### Post by Milambar on 2010-07-27
I have a two small scripts, one generates a datafile, the other uploads it to a webserver. Lets call them generate.sh and upload.sh

I want them both to run every 5 minutes, but, I want upload.sh to run 1 minute after generate.sh.

Getting generate.sh to run every 5 minutes is easy, its just
*/5 * * * * generate.sh

However, how do I get upload.sh to run 1 minute later, I can't do */6 because then it'd run every 6 minutes. I can't do */5 because then it'd upload a file that hasn't been generated yet.

Any suggestions welcomed.

---

### Post by rubylaser on 2010-07-27
Why don't you just call sleep 60 then run your upload.sh at the end of your generate.sh script?

---

### Post by rnerwein on 2010-07-27
> **rubylaser said:**
> Why don't you just call sleep 60 then run your upload.sh at the end of your generate.sh script?

hi
that's the only and the easiest way to do it - plus 1.
ciao

---

