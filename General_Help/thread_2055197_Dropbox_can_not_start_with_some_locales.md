---
title: "Dropbox can not start with some locales"
date: 2012-09-08
forum: General Help
---

### Post by rkoma on 2012-09-08
On Ubuntu 12.04 and probably some other versions Dropbox can not start on some locales. Particulary sr_RS is causing problems, possibly there are other. Cause of the problem is in the unsupported locales in the python.

Python version 2.7 does not have this problem, however, it seems that Dropbox is compiled with some older version, so the problem still persist even if you have latest python installed.

The solution is to change locale to some supported in the Dropbox startup script:

```
~/.dropbox-dist/dropboxd
```

Just prior to starting dropbox, add code for changing locale. The following works for me:

```
if [ "$LANG" = "sr_RS" ]; then
  LANG="sr"
fi
```

The above changes locale from unsupported sr_RS to the same, but supported sr. Fix should be changed to the appropriate locale. Dropbox now works smoothly.

---

