---
title: "How to make s2ram to be default suspend method?"
date: 2010-09-08
forum: General Help
---

### Post by thewk on 2010-09-08
I have Acer Travelmate 5520 laptop and Ubuntu 10.04. There are problems with suspending and waking from it with the default settings Ubuntu has. I Googled about solutions and found that uswsusp is able to put the machine to sleep and wake succesfully. How could I configure it to be the default method to put the machine into suspend? Right now it only works via command line with command:

sudo s2ram -f

I have to use -f because my machine is unknown model for uswsusp. If I press the sleep button or put the machine to sleep by closing the lid, it certainly does not use uswsusp because the sometimes crashes when going into suspend or at wakeup, mouse also disappears. With s2ram command everything works.

---

### Post by pbrane on 2010-09-08
have a look at this:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1549411]("http://www.uluga.ubuntuforums.org/showthread.php?t=1549411")

be sure to read the link in the last post.

---

