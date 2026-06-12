---
title: "Privacy - Hulu stays logged in after deleting cookies and Flash files"
date: 2009-12-29
forum: General Help
---

### Post by Deng10 on 2009-12-29
I've done my best to search the web to find any hints to what could explain this behavior without any mention, I'm hoping someone here may give me an idea.  This problem is probably with either Firefox or Flash, I don't know if specific to Ubuntu or cross platform.  I'm hoping this isn't excessively off topic. 

Here is what I am doing: I log in to Hulu, then leave the site, use Firefox's Clear Private Data... function with all boxes checked.  I then shut down the browser, open a terminal and go to ~\.macromedia\Flash_Player and execute rm -r * to delete anything it could be leaving on my computer.  I then reboot the system, in case there is some cached copy of anything that is still accessible.  After the reboot completes, I navigate to hulu.com and the site still recognizes me.  

I'm a privacy / security conscious person and I can't figure out what trace is being left on my machine that Hulu is using.  Clearly whatever they are doing could also be used by ad networks, phishers or whatever other undesirable tracking entity exists out there.  Am I missing something?  Can others reproduce my results?  I'm running 8.04 Hardy Heron, Firefox 3.0.16 and Flash 10.0 r32

---

### Post by scouser73 on 2009-12-29
It sounds as if the problem is on Hulus' end.  I would assume that the session doesn't end on their part even though you have deleted the cookies.  Perhaps visiting the [[COLOR="Red"]**Hulu Support Page**[/COLOR]]("http://www.hulu.com/support") might offer you a better solution to the problem.

---

### Post by Deng10 on 2009-12-30
Interesting idea, but that can't explain the behavior I'm seeing.   The length of time between visits to Hulu (and in fact, length of time of even having this PC turned on) has been several days.  I can't imagine that a session is being revived across nearly a week.  I also have other PCs behind the internet facing router, so it can't be based on IP address, since the other PCs do not get the auto-login behavior.

There must be some file being left on my machine, I just can't figure out what.

---

