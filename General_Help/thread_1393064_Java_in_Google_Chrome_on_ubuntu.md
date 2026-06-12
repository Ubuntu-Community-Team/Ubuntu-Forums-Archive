---
title: "Java in Google Chrome on ubuntu"
date: 2010-01-28
forum: General Help
---

### Post by Zorgoth on 2010-01-28
I just resurrected an ancient computer by installing Ubuntu on it and i am using google chrome because it is lighter, but so far i have not found a way to install Java on it, which apart from finding some pair of ancient speakers to go with my ancient computer is the last thing I have to do to make this a workable internet and word processing machine.  How do I do this?

---

### Post by zvacet on 2010-01-29
Did you install java-plugin?

```
sudo apt-get install sun-java6-plugin
```

---

### Post by Zorgoth on 2010-01-29
Got it working.  Thought i had plugin installed but didn't.

---

### Post by scouser73 on 2010-03-01
I've just installed the latest version of Java on Google Chrome with this tutorial: [[COLOR="Red"]**Install The Latest Version Of Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

Although that it's a tutorial for installing the latest version of Java on Firefox, it does work on Google Chrome as long as you still have **~/.mozilla/plugins** in your home directory.

The final test when I'd installed Java was to close Google Chrome and restart it and enter **about:plugins** in the address bar which shows that Java has been successfully installed.

Screenshot.

[IMG][[IMG]http://img64.imageshack.us/img64/6263/screenshotna.th.png[/IMG]](http://img64.imageshack.us/my.php?image=screenshotna.png)[/IMG]

---

