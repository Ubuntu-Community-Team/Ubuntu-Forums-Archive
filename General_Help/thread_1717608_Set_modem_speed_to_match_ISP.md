---
title: "Set modem speed to match ISP"
date: 2011-03-30
forum: General Help
---

### Post by tfultz33 on 2011-03-30
I  live in the boonies and I have dial up. Whats worse is the ISP has a limiter on the server which cuts the speed down to 26.4 k. Every time I download and the speed gets over that, the modem pauses then starts again. It sucks. If I could just have a steady stream I would be better off.

I am using a Linuxant type hsfmodem hybrid. How can I slow the speed down on the modem so it doesn't jump over 26k so much ?

I tried adjusting the baud which shortens the duration of the pause, I think, but when I go lower it actually makes it longer. 

Thanks for any help.

---

### Post by mikewhatever on 2011-03-30
Not quite what you are looking for, but if you could download with wget, then 'wget --limit-rate=24K' would come handy. DownThemAll, a download manager extension for Firefox also has that same functionality.

---

### Post by tfultz33 on 2011-03-30
Thanks for your reply.
I will give that a whirl, but I was looking for a solution to limit the connection speed as a whole.

Of course, this may not even be the problem. I t could just be how my modem responds with this driver, or the crappy phonelines or countless other things. 

Thanks again. I will try it.

---

