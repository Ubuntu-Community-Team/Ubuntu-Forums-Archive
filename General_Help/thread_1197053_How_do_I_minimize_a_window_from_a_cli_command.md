---
title: "How do I minimize a window from a cli command?"
date: 2009-06-25
forum: General Help
---

### Post by kloplop321 on 2009-06-25
Well I have a mouse issue on my laptop, which I fix through disabling it through an xinput command. I have no problem with that. However, The hardware ID seems to swap some times if I come back out of sleep mode. I fixed this by a php script that loops in the background every 10 seconds.(It works very well, and does not take up any meaningful amount of resources.) However, The only way I can get it to run is by starting it in a terminal. SO I am using xterm to execute it. 

Here is the problem: how do I make xterm minimized when started? I can do the opposite(maximize), but I would like to minimize it(or at least send it to the second workspace). 
Is there a terminal command I can run to do this also, or is there another optional input that I can use to do this?

EDIT:
I just needed to do "-iconic" 
I didn't know what it meant, but I tried it and noticed I did not see it, but it appeared at the bottom, and it seems that makes it minimized.

---

