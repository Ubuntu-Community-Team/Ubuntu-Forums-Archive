---
title: "wget and httrack problems"
date: 2009-10-18
forum: General Help
---

### Post by raywood on 2009-10-18
I'm using webhttrack to download some websites.  It seems to be going OK for most of them.  One of the websites is private, i.e., requires a password.  I know the password, but am I correct in finding no option to enter a password in httrack?  I'm using the GUI version - maybe the command-line version is different?

I'd just go ahead and try the command line version, but I'm already trying the command-line version of wget, and that isn't working either.  Here's what I'm entering:

```
wget -mrc --convert-links --progress=dot --http-user=[account name] --http-password=[account password] --level=3 --page-requisites --no-parent http:[URL]
```

When I enter that, I get repeated statements of "Read error at byte 15923/15468 ((null))."  What am I doing wrong?

Many thanks, many cheers ...

---

