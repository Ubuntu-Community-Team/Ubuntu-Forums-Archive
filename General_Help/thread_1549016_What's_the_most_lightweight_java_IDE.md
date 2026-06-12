---
title: "What's the most lightweight java IDE?"
date: 2010-08-09
forum: General Help
---

### Post by imakbari on 2010-08-09
Hi,

I bring my netbook where ever I go, so I use it for programming all the time. I used to have windows 7 on it and Java Eclipse worked fine and fast for me. but recently, I formatted the hole hard disk and installed ubuntu (cause I was sick of windows 7, of course)
While using ubuntu, Java Eclipse works slower than how it worked on windows.
so i was wondering if there's a Java IDE for ubuntu (10.04) which is faster and more lightweight than eclipse. In fact, I'm looking for the most lightweight Java IDE.
(I have a Toshiba NB200 with 1 GB of RAM)

tnx in advance.

---

### Post by lykeion on 2010-08-12
The most lightweight solution is to not use an IDE at all, just a text editor and build and run from command-line.

I use **_[IntelliJ Idea CE]("http://www.jetbrains.com/idea")_** for Java development and it works fine for me. 
Ok, the startup is a bit slow and the step debugger isn't lightning fast, but otherwise it suits all my needs, and is by far the best IDE for Java development IMO.

You could also try out **_[JEdit]("http://www.jedit.org")_** which is in the repository:
sudo apt-get install jedit

You say you got 1 GB RAM and you feel that Eclipse is sluggish. It should run fine with half of that RAM, so maybe it could be something other going on.
You should check how much RAM and CPU Eclipse uses with top or htop:
_[http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/](http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/)_

Hope this helps...

---

