---
title: "Limit skype memory usage?"
date: 2012-09-30
forum: General Help
---

### Post by Ashrael on 2012-09-30
Hi all,

I have had this problem on and off since the beginning with skype: Sometimes it just eats all my memory and swapspace and then it crashes.... This whole process takes about 10 minutes to complete.

Now my question is: Can I limit the maximum amount of memory that skype uses, and how?

I have seen some general info about how to do this, but I'd rather have some specific info before I try it.

Thanks!

---

### Post by ryanyeah on 2012-09-30
I don't know about memory in particular, but you could look into using the 'nice' command. It will let you give priority to certain processes and thus you could give skype a lower priority to operate so it doesnt use all your resources.

---

### Post by Ashrael on 2012-11-17
No, I really need to limit the ammount of ram and swap avaiable to skype. I have checked it when it goes al weird on me and it does eat up all my ram and then all my swap, changeing the "nice'ness isn't gonna change a thing, well maybe it will crash a bit faster :)...

So anyone got way of doing this?

---

### Post by blackbird34 on 2012-11-17
I did a google search and found this [http://unix.stackexchange.com/questions/44985/limit-memory-usage-for-a-single-linux-process](http://unix.stackexchange.com/questions/44985/limit-memory-usage-for-a-single-linux-process) but it seems a  bit technical, i'm out of my depth for one :D Several commenters on the question posted supplementary links though!  Also see [https://en.wikipedia.org/wiki/Cgroups](https://en.wikipedia.org/wiki/Cgroups)  good luck!

---

