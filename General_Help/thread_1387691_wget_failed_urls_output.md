---
title: "wget failed urls output"
date: 2010-01-22
forum: General Help
---

### Post by sgordon on 2010-01-22
Hey all

I'm using wget to retrieve a long list of URLs, a small proportion of which fail, hence:

```
wget --input-file=urls.txt
```

Is there a way to log the urls that have failed? Unfortunatley wget does not output the current URL being processed (and then the status), so hard to see grepping the output helping.

Or should I use some alternative like curl, wmget?

Thanks!

  Si

---

### Post by KeLa on 2010-01-22
Add either of following to the command
```
--append-output=logfile
```or
```
--output-file=logfile
```
So you get log of what wget does.

---

