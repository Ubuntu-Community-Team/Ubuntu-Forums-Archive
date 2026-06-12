---
title: "chmod and wildcards?"
date: 2009-07-18
forum: General Help
---

### Post by Piraja on 2009-07-18
Dear all,

I tried to change permissions in a subdirectory using "chmod 400 VIDEO_TS/*" but (the current version of) chmod does not seem to understand wildcards, as in this example:

```
sudo chmod 400 VIDEO_TS/*
chmod: cannot access `VIDEO_TS/*': No such file or directory
```

I was following [Brandon Hutchinson's tutorial]("http://www.brandonhutchinson.com/Burning_Video_DVDs_in_Linux.html") and was surprised at this problem. I had to change the permissions file by file, one by one – I'm not sure, though, if navigating to the subdirectory and doing "chmod 500 *" there would have worked... **[EDIT, some 5 min later:]** Yes, that did it! But I wonder if the use of wildcards following a slash is a deprecated function in chmod.

---

