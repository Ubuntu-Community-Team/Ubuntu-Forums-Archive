---
title: "Firefox on Ubuntu going weird?"
date: 2010-07-13
forum: General Help
---

### Post by PhysicsAstronomy on 2010-07-13
Hello,

I'm an Ubuntu newbie (I've been using it for only about a week) and so far I haven't had too many problems.  However, yesterday my Firefox went strange for a bit.  Instead of loading the Ubuntu Google start-up page as usual, it went to a page I had never seen before.  Since I was doing multiple things, I can't quite remember the address, however something similar happened this evening.  Since I don't remember exactly how it happened yesterday, I can't be sure what happened today is exactly the same.  Today though, it went to an address called "about:home" at which it gave a 404 error.  I've done a bit of research on various sites and have never seen where anything called "about:home" even exists.  However, when I type in other about: addresses that I don't think exist it just gives me an error message saying that the requested address does not exist.  It does not give a 404 error.  I have absolutely no clue what's happening.  The odd start-up happens even when you close the program and restart it, however a few minutes later it works again as if nothing is wrong.  Today, I also noticed that the red warning triangle that tells you have updates has appeared.

I would very much appreciate if anyone else having these problems writes a comment to let me know its not just my computer's problem.  Also, if any expert out there knows why its happening, I would also very much appreciate the help.  

Thank you for helping a newbie out...

---

### Post by PhysicsAstronomy on 2010-07-13
by the way, in case this helps, i'm using Ubuntu 10.04 on Oracle VM Virtual Box.

---

### Post by borth92 on 2010-07-13
about:home is the default home page that comes with firefox. I do not know why it reverted to original settings or why it gives an error when it attempts to go to about:home. I would use synaptic package manager to remove and reinstall firefox. or you can open a terminal and type (without quotes)
"sudo apt-get remove firefox"
"sudo apt-get install firefox"

---

### Post by mikewhatever on 2010-07-13
When I put about:home into the address bar, I get to the default home page, [http://start.ubuntu.com/10.04/Google/](http://start.ubuntu.com/10.04/Google/).
Firefox uses quite a few of these about:XXX, for example:
```

about:mozilla
about:plugins
about:config

```
About:home doesn't look too special after these.

---

### Post by PhysicsAstronomy on 2010-07-13
thank you both for helping.  i also don't know what the problem was.  my internet worked just fine on Windows.  only in my virtual box did the 404 error come up.  as for what comes up when i type about:home, i will try it after reinstalling Firefox.  Again, thank you...hopefully it will work well when i reinstall.

also, there is also an about:robots

---

