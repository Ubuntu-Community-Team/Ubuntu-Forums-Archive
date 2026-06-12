---
title: "Proper boot progression"
date: 2009-07-05
forum: General Help
---

### Post by ericstrom on 2009-07-05
What is the proper sequence for Jaunty boot up. Should the splash screen come up and stay up while going through all the steps involved in booting or should it come up for a while and then disappear and the screen go black until Jaunty is fully up and the welcome sound starts ?

I currently get the splash screen for 10 to 15 seconds and then the screen goes black (with the exception that I see my cursor) for another 20 to 25 seconds. After that period I get the welcome sound and Jaunty is up and running. Is that the way it's supposed to work or is there a bug in the boot sequence somewhere ? It seems odd that the splash screen would disappear and go black for 20 to 25 seconds.

---

### Post by sdennie on 2009-07-05
There is a certain point where X needs to initialize your graphics hardware and sometimes that can take some time.  20-25 seconds sounds like a long time but, gdm is started fairly early in the boot sequence which means that a lot of other things are going on in the background at the same time.  If you have an older computer or a slow disk, 20-25 seconds is certainly possible.

---

### Post by ivanvajar on 2009-07-05
You posted this on another place. There is nothing wrong with your boot time.

---

