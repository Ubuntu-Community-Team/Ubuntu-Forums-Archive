---
title: "Extreme slowdown in ubuntu?!"
date: 2009-10-22
forum: General Help
---

### Post by Tibco on 2009-10-22
I recently moved onto karmic beta and i still have a problem thats been bugging me since jaunty. My laptop will randomly slow down, so slow that it becomes unusable. This happens when ever, i haven't found any thing specific that causes this. I ran 'top' and i found out some things. Whenever the slow down occurs, there appear to be a ton of instances of 'w -hs' and also 'pidof' running. When i mean a ton, i mean they take up the entire list on 'top'. My cpu goes to 100% and my load levels increase to 500-1k+. Also, ubuntu starts chewing up more than 2GB of ram!! What is going on here?

PS, i couldnt find any other cases like this one, so im at a loss on what to do. This does not happen in vista, and i dont think its a hardware problem as my laptop is almost brand new.

---

### Post by kbielefe on 2009-10-22
The first thing I would do is try to find the process that is spawning all of those.
```
$ ps axo pid,ppid,cmd
```Find the ppid for all your trouble processes, then find the process with that as it's pid, continuing to trace back as many levels as necessary until you see something that isn't w or pidof.  That should give you a starting point to look at.

---

### Post by Tibco on 2009-10-22
Ok, i'll take a look the next time my system slows down. in the mean time, does anyone else have this problem? Its been bugging the crap out of me.

---

### Post by Tibco on 2009-10-25
Problem Fixed, it appears that all those spawned instances were created by an option in laptop-mode that i set on. It was called something like battery level polling; but once i turned that off, everything was running normal! Thanks for the tip, otherwise i would never have figured it out!

---

