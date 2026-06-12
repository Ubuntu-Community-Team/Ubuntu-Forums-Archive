---
title: "Imagemagick automatic Screenshots script PROBLEM"
date: 2011-02-19
forum: General Help
---

### Post by niko32 on 2011-02-19
I found somewhere on internet this script for taking screenshots of desktop every 5 minutes:

```
#! /bin/bash
#file: screenshot.sh

if [ $1 ]; then
appenddate=_$(date +%d%b%y-%N)
fi

while [ 1 -eq 1 ]; do
import -window root ~/screenshot$appenddate.png
sleep 5m
done
```

I've put it in startup, made it executable and **it is working, but not quite right**?
Actually it is taking screenshot every 5 minutes but it's not appending a date to a filename so it's **constantly overwriting old one** and all that is left is just one file: **screenshot.png** in my home folder.

I've tried a few changes but I'm afraid I'm not very skilled in this. If anyone knows what is wrong with this script I would be grateful. :)

---

### Post by TheHackOps on 2011-02-19
> I've tried a few changes but I'm afraid I'm not very skilled in this. If  anyone knows what is wrong with this script I would be grateful
How is he going to know what any of your edits mean...

---

### Post by niko32 on 2011-02-20
> **TheHackOps said:**
> How is he going to know what any of your edits mean...

That is an original script as I found it. I didn't post any of my unsuccessful edits.

I guess someone with experience could notice why this script doesn't append date to filename. There must be some error in this script, but I can't figure it out.

---

### Post by ajlee on 2011-12-27
**EDIT:** Just realized how old this post was... you probably don't need this anymore - but maybe it will help someone else.

Your problem is with the while loop.  Your date gets set at the top, once you enter the loop it never gets updated again.  You'd be better off doing something like this:

```
#! /bin/bash
#file: screenshot.sh

appenddate=_$(date +%d%b%y-%N)

import -window root ~/screenshot$appenddate.png


```

and just setting it in cron to run every five minutes instead of using the loop/sleep logic.

---

