---
title: "browser launcher script stopped working"
date: 2011-02-20
forum: General Help
---

### Post by zorblek on 2011-02-20
I use several different browsers, and I don't have a lot of memory, so I try to only have one open at a time. I wanted web pages to open in whatever browser was open at the time, so I created a shell script and set it as the default browser. It checks to see if any other browsers are running, and if not, it opens the page in Swiftfox (an optimized version of Firefox). This worked for quite a while, but recently it stopped working. Now it opens URLs in Swiftfox regardless of what else is running, and I can't figure out why. As far as I can tell none of the process names have changed, and I haven't edited the script. I'm not very experienced with scripting, so I'd really appreciate any help or insight. Thanks!

The script:
```
#! /bin/bash

if pidof swiftfox-bin
then swiftfox $*
else if pidof firefox
then firefox $*
else if pidof google-chrome
then google-chrome $*
else if pidof opera
then opera $*
else swiftfox $*
fi
fi
fi
fi
```

---

### Post by tredegar on 2011-02-20
> Now it opens URLs in Swiftfox regardless of what else is running

Perhaps there is an instance of swiftbox already running?

Check with ```
ps -Al | grep swift
```
Otherwise, debug your script by trying each line, one at a time, from a terminal eg

**pidof firefox**

(which does not work for me I have to do **pidof firefox[COLOR="Red"]-bin[/COLOR]** to get the PID

I'm running 10.04.2

---

### Post by zorblek on 2011-02-20
Well, it turns out that I was wrong on two counts: I missed the firefox issue (I hardly ever use plain firefox, so I never noticed) and at some point the main Chrome process changed from google-chrome to just chrome, and I didn't notice.

Thanks so much for the help! This was a major annoyance while it lasted.

---

### Post by tredegar on 2011-02-20
Thanks for the follw-up. Pleased you got it fixed.

---

