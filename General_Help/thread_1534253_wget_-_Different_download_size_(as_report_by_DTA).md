---
title: "wget - Different download size (as report by DTA)"
date: 2010-07-19
forum: General Help
---

### Post by fly-by-night on 2010-07-19
When I download a file in wget it show the file size as what I understand to be:  **space on disk** & **(file size)**(whatever it's called is irrelevant).
```
Length: 366981450 (350M)
```

The amount downloaded appear to be the first which is bigger.
```
100%[++++++================================>] 366,981,450
```
In Downthemall the reported size is **350MB**.  It download to 350MB(?) as far as I can tell.

 Obviously I can't be downloading more.  The only thing I can think of is that wget's counter moves faster than DTA's since it show the bigger size.

However when I use a stopwatch to measure the time it take to download 2.000.000 bytes (roughly) it's similar. (my connection is slow enough to allow for that - 384kbps).

Am I missing something?

---

### Post by The Cog on 2010-07-19
366981450 / 1024 / 1024 = 349.98

So I think Downthemall is dividing by 1048576 instead of 1000000 and calling it MB. I think it should be called 367 MB since it's very close to 367 million bytes, but a number of youngsters who've never done engineering seem to think a million is 1048576. But that's a flame war that could do without restarting here. The real truth can be got at by looking at the actual size of the saved file and I'm sure the byte count shown by wget is correct.

---

### Post by fly-by-night on 2010-07-19
Your calculations make perfect sense.   I was thinking in a totally different direction and forgot the basics of MB to bytes.  
That would also explain why both speed calculations on 2MB (or MiB) was the same (it get to 1000kB in the same time, just displayed differently).

Thank you.

---

