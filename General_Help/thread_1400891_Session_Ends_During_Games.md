---
title: "Session Ends During Games"
date: 2010-02-07
forum: General Help
---

### Post by Jojochinoise on 2010-02-07
I hope someone can help me.... Whenever I play a desktop game, my session ends, prompting me to login again. Why does this happen? How can I fix it?

---

### Post by Mark Phelps on 2010-02-07
Would help if you could provide us some details ...

Such as WHICH game?  Name, version.

Is this a Linux game? Or are you trying to play an MS Windows game using Wine?

And what do you mean "session ends"?  Does the machine crash?  Are there error messages?  Does the machine reboot?  Does it logoff?

---

### Post by Jojochinoise on 2010-02-07
It seems to happen during ANY Linux game that I launch from the menu. As I said before, I get prompted to log in again, so yes, my session logs off. This hasn't happened any other time, ONLY when playing a game. Is there anything I can do?

> **Mark Phelps said:**
> Would help if you could provide us some details ...

Such as WHICH game?  Name, version.

Is this a Linux game? Or are you trying to play an MS Windows game using Wine?

And what do you mean "session ends"?  Does the machine crash?  Are there error messages?  Does the machine reboot?  Does it logoff?

---

### Post by Nosferax on 2010-02-07
This has been happening to me as well. Session goes black, and I see the Ubuntu loading screen as if I was booting my computer. I then see the login screen. Takes about 4-5 seconds to go from crash to login screen.

It was not when playing games however. It happened when starting the  compilation process of a game.

It has happened thrice to me so far since last week, never before. The last thing output in my dmesg log are the following : 

First crash :
> [ 4060.772040] glxinfo[4385]: segfault at 8275694 ip 00cccc22 sp bfb5f0c0 error 6 in libc-2.10.1.so[c5f000+13e000]

Second crash :
> [ 5698.993880] compiz.real[4423]: segfault at 378 ip 08055c3c sp bfe0de30 error 4 in compiz.real[8048000+34000]

First one clearly has to do with openGL and the like. Second one is more confusing. I have disabled compiz and will see if it still crashes. Maybe we have the same problem, maybe we don't. 

What surprises me is that the whole session crashes, how come ? How can one faulty process (clearly the build in my case) crash the whole computer/session ? 

Let me know if I should start a new thread for this. I just google'd 'ubuntu session crash' and this seemed to be the most relevant post. 

Thanks,
Nox

---

