---
title: "Why does confirmation of wrong password takes so long time?"
date: 2011-02-18
forum: General Help
---

### Post by Svens on 2011-02-18
I am just wondering, why is it so that when you enter a wrong password at the login screen it takes about 2 seconds for Ubuntu to answer that the password is incorrect? When you enter the password correctly, Ubuntu understands it in less than 0,1 sec and your'e welcome to your desktop. 
I am sure that Ubuntu understands that password is incorrect as fast as it understands that the password is correct. How it would be possible to change the time Ubuntu "checks" wrongly inputed password?
I hope my thought is clear and you understand me. :)
Have a nice day!
Thank you! :)

---

### Post by rg4w on 2011-02-18
There may be a lot of things contributing to that, but I'll bet at least half a second or more is purely an arbitrary wait to thwart brute-force attacks.  You'll see a similar wait period in many registration windows for proprietary software.  Even a modest half-second wait can turn a brute-force crack that might have taken hours into one that can take weeks.

---

### Post by 3Miro on 2011-02-18
If your machine is fast enough, I can hit it with hundreds if not thousands of passwords per second. It may not be to long before I hit the right one. Making me wait a second before attempts, prevents such an attack.

---

### Post by Svens on 2011-02-19
Thank you for your explanation! Didn't think about that from that point of view! Now it's clear. :)
Thank you rg4w and 3Miro!

---

### Post by hakermania on 2011-02-19
I had the same question once and yes, this is the answer....
but it is annoying, isn't it?
sudo could log the sudo attempts and if there are 3 wrong attempts, so to understand that probably something goes wrong and for 5 minutes it could have the delay and then again without the delay and if 3 wrong attempts again 5 minutes the delay and so on, it's no use having the delay always...

---

### Post by rnerwein on 2011-02-19
> **Svens said:**
> I am just wondering, why is it so that when you enter a wrong password at the login screen it takes about 2 seconds for Ubuntu to answer that the password is incorrect? When you enter the password correctly, Ubuntu understands it in less than 0,1 sec and your'e welcome to your desktop. 
I am sure that Ubuntu understands that password is incorrect as fast as it understands that the password is correct. How it would be possible to change the time Ubuntu "checks" wrongly inputed password?
I hope my thought is clear and you understand me. :)
Have a nice day!
Thank you! :)

hello

normaly there is a resolution for your problem - but not in ubuntu ( i tried it, even after i changed the file
/etc/login.defs).
there is a option called: FAIL_DELAY=nn-seconds
but it don't works on my system (10.10). it works on suse.
may be there are a couple of files to change. but the only way to change it on different other systems was
to change this option.
but in mind - other people told you --> even if it possible --> don't decrease that limit --> if there is a way
to set it higher --> that's ok.
ciao

---

