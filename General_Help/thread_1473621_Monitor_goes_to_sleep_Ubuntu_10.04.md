---
title: "Monitor goes to sleep Ubuntu 10.04"
date: 2010-05-05
forum: General Help
---

### Post by nmyrick on 2010-05-05
I have Ubuntu 10.04, and I have my power settings set so that my display is never supposed to go to sleep, yet it still does after 10 minutes of being idle.  Has anyone else had this issue?

---

### Post by scouser73 on 2010-05-05
Try Caffeine to keep your monitor on, use these command in Terminal.

> **sudo add-apt-repository ppa:caffeine-developers/ppa**

> **sudo apt-get update**

> **sudo apt-get install caffeine**

Caffeine can be used upto 168 hours & 59 minutes before the screen turns to power saving mode.

I use it on my pc as I was fed up of the screen going black when I was watching a film.

---

### Post by ranch hand on 2010-05-05
Are you sure that the screen saver is not kicking in?  By default it is set to a black screen and to lock the screen.

Unchecking the box in your screen saver settings that locks the screen stops this problem.

---

### Post by nmyrick on 2010-05-05
Thanks, it was the screen saver.  Didn't think of that.  I didn't have the issue until I installed 10.04.  I had 9.10 before and I didn't have this issue, so I didn't think about that.

---

### Post by ranch hand on 2010-05-05
Yes they changed the default setting.

You should mark the thread "solved" using "Thread Tools" at the top of the page.  This helps folks who may have advice not waste their time and folks who may have a similar issue.

Glad you are running all right now.  That one never bothered me as I always go to the screen saver first thing after an install and from the link on it to the power manager.  It did catch a lot of people in testing though.

---

### Post by learning_ on 2013-01-23
> **scouser73 said:**
> Try Caffeine ... 

THANK YOU FOR THIS! I've been scouring the interwebz for literally months (off an on of course but still, a long time) trying to find a solution to this. Found out about caffeine recently but couldn't find a method to use it in 10.04. Thanks a lot =]

---

### Post by oldos2er on 2013-01-23
Old thread closed.

---

