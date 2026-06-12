---
title: "No sound after resuming from suspend"
date: 2010-05-30
forum: General Help
---

### Post by whalogreg on 2010-05-30
Before upgrading to 10.04 from 9.10, I had sound issues after resuming from suspend (I had no audio at all). I found a script that solved the sound issue. My problem now is, with 10.04, the script keeps my laptop from going into suspend. I haven't been able to find anything to resolve this issue in 10.04. Any help as to why/how to resolve?

---

### Post by whalogreg on 2010-06-01
bump

---

### Post by compyprog on 2010-06-01
What script are you using? I am having a similar problem and I wonder if you are using the same one as me.

---

### Post by whalogreg on 2010-06-01
> **compyprog said:**
> What script are you using? I am having a similar problem and I wonder if you are using the same one as me.

The script is named "10_sound-after-resume" and it runs this code

```

#!/bin/sh
/sbin/alsa force-reload

```

it said to place it in the directory /etc/pm/sleep.d/

Worked flawlessly in 9.10, but after upgrading to 10.04 it kept my system from ENTERING suspend..

---

### Post by inameiname on 2010-06-01
I've had this problem as well, it have also tried this solution, and it also doesn't work in Lucid for me either.

Nobody seems to have figured it out. 

FYI, here are a few other things I've tried that I've found in my search of a solution (I wrote them out in this thread):

[http://ubuntuforums.org/showthread.php?t=1475616](http://ubuntuforums.org/showthread.php?t=1475616)

---

