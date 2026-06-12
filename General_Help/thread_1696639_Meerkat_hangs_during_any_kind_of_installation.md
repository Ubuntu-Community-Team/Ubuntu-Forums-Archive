---
title: "Meerkat hangs during any kind of installation"
date: 2011-02-27
forum: General Help
---

### Post by Shamgar13 on 2011-02-27
Hello all.  I've been a long time lurker around here and this is my first post.  I've just installed Ubuntu 10.10 on an eMachines EL1200.  The installation itself went without any problems.  However, when I attempt to install anything else, the entire system will freeze, and force me to restart the computer manually.  Any thoughts?  I'm still relatively new to Ubuntu, so if you would like logs or things of that nature I'll need to know what to input into the terminal.  Thanks in advance!

---

### Post by snowpine on 2011-02-27
Which package, specifically, are you trying to install, and how?

Let's try installing that same package from the terminal (I'll use "firefox" for the sake of argument, but obviously you should replace "firefox" with the name of your application).

```
sudo apt-get update
sudo apt-get install firefox
```

You can copy & paste the results from the terminal into your forum reply, so we can take a look and help you troubleshoot. :)

---

