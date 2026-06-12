---
title: "Swap file growing uncontrollably"
date: 2010-05-20
forum: General Help
---

### Post by Diskbox on 2010-05-20
Hi

I've looked around the forum and done some web searches but haven't found the answer yet so posting here.

Currently running 10.04 and Cacti latest version and although my RAM is only just over 3/4 used my swap file is growing.  If I leave the box running for about a week the swap fills and the system grinds to a halt.

Is there some way of seeing what's in the swap so I can debug the problem and get my system more stable again?

Thanks,

Diskbox

---

### Post by john newbuntu on 2010-05-20
These two commands should give an idea on the swap filesystem and usage:
swapon -s
free -m

---

### Post by dino99 on 2010-05-20
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Diskbox on 2010-05-20
Thanks for the replies.

I think I should have been a bit more specific in my original request for help.
I'm trying to find a command/program to show me the processes/programs which are currently swapped into the swap file.

Alternatively, is there a better way of identifying where the memory leak is on my system and why the swap file just keeps filling up?

Thanks again,

Diskbox

---

### Post by dino99 on 2010-05-20
right click on the top panel and install system-monitor, then ckicking on its icon you can view all the activity in live

---

### Post by srs5694 on 2010-05-20
From the command line, you can use "top". Just type "top" and then type "m" to sort by memory use. That will show you what programs are consuming the most memory (RAM and/or swap space).

---

