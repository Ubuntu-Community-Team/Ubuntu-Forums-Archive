---
title: "Empathy not connection to icq for a few days now."
date: 2011-06-13
forum: General Help
---

### Post by t.rei on 2011-06-13
Hi.

Does anyone have the same problem, and maybe a solution to this?

Would be grand.

---

### Post by highmighty on 2011-06-13
Same issue here

---

### Post by katastrophenschutzplan on 2011-06-13
Hi t.rei, 
> **t.rei said:**
>  Does anyone have the same problem, and maybe a solution to this? 
Well, yes. not me, but a friend of mine (ubuntu 11.04).
I found this link: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/795932](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/795932)
And maybe comment #5 will help you.
Please report :)

bye

---

### Post by Heretic666 on 2011-06-14
> **katastrophenschutzplan said:**
> Hi t.rei, 

Well, yes. not me, but a friend of mine (ubuntu 11.04).
I found this link: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/795932](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/795932)
And maybe comment #5 will help you.
Please report :)

bye

Yes, it worked for me. Thank you.

---

### Post by t.rei on 2011-06-14
Doesn't work with empathy 3.1.1

At least the problem is clearly seen - post #10:
"Problem is with libpurple's default client key. It looks like it's  blocked now by ICQ servers. If you changed it to for example client key  used by pidgin it will be working again."

So either compile it oneself, or wait for an update. 

Well maybe this helps convince even more people that icq just plain stinks. -.-

---

### Post by j_m_w on 2011-06-15
> **t.rei said:**
> Doesn't work with empathy 3.1.1

At least the problem is clearly seen - post #10:
"Problem is with libpurple's default client key. It looks like it's  blocked now by ICQ servers. If you changed it to for example client key  used by pidgin it will be working again."

So either compile it oneself, or wait for an update. 

Well maybe this helps convince even more people that icq just plain stinks. -.-

i dont run 3.1.1 but the hint from the other thread post #5 didnt work for me aswell.

another one posted: 
```
mc-tool update `mc-tool list | grep icq` string:encryption=no_encryption
``` 
and that worked for me.

give it a try

---

