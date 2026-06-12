---
title: "Games on Ubuntu"
date: 2011-12-31
forum: General Help
---

### Post by Lyrik on 2011-12-31
Sorry if this thread has been posted before but I couldnt find on similar to what I am pondering.

Is it possible to edit the coding of a game or other program, or do something to it, that will make it run on ubuntu when it was made for windows?

---

### Post by whatthefunk on 2011-12-31
You can use Wine.

---

### Post by Synoc on 2012-01-01
wine will run A LOT of programs. not all programs and quite often a wine update or a game update will force you to fix things again. Play on Linux is good. you can go to their website and take a look as well. Ragnarok ONline is one of them (according to their website)

---

### Post by rsvancara on 2012-01-01
It is possible to edit the source code to run games on Linux.  But most games are proprietary in nature and will not release their source code to be used on Linux.  Also, some games use DirectX exclusively, which is a Windows API developed specifically for the windows environment.  

Wine implements the DirectX api to allow games to function on Linux, however, it is not 100%  in terms of functionality and often you may observe artifacts or impacted game play.  

Some games use OpenGL, which has more cross platform support.  DirectX provides an "abstraction layer between" openGL which can make it easier for game developers to build games.  

So to answer your question, you can edit the code if you have access to it.  Most game companies do not release the source code to their games.  Wine is a great alternative and it supports more applications all the time.  It is not the true answer to bringing games to Linux, but it is a great start and they have great support through their community.

Best of luck!!

---

### Post by syerges on 2012-01-01
another option is to install virtualbox and windows on it in order to play the game. It is often the easiest solution as Windows is a gaming OS.

---

### Post by Synoc on 2012-01-01
> **syerges said:**
> another option is to install virtualbox and windows on it in order to play the game. It is often the easiest solution as Windows is a gaming OS.

this is an option provided you have a working copy of windows, with activation key. the downside is, that anything that requires high graphics will most likely not work well or anything that requires a lot of RAM. as video card drivers are not supported by virtualbox (natively) and RAM is limited to whatever you set it to.

---

### Post by guyver_dio on 2012-01-01
Just use wine with a management tool like playonlinux or winetricks. 

I don't know about hacking code but there was one trick we use to use back in the day. Where if a game couldn't get past the installer in wine, we'd install it on a windows pc then copy the folder over to the fake c drive that wine sets up. Then you can try running the game exe using wine and see if it launches. 

If you just can't live without a game and really need it to work, I'd go with dual booting windows over running windows in virtualbox. Unless your pc is pretty high spec, newer games probably won't run that well.

---

### Post by Mark Phelps on 2012-01-02
> **Lyrik said:**
> Is it possible to edit the coding of a game or other program, or do something to it, that will make it run on ubuntu when it was made for windows?

My guess is that you're asking about some kind of "patch" that could be applied to an existing Windows game to get it to run in Linux.  And, in that case, the answer is NO.

OF course, you could REWRITE the game -- but that's about as practical as rewriting MS Office to run in Linux -- and not doable since game sellers and MS are not about to release their source code.

You should check the WineHQ website, look up your particular game and version that you want to run -- and see the ratings.  Anything not rated, or rated silver or lower, is most probably NOT going to work.

---

