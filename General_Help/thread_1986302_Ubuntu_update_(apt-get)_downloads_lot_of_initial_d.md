---
title: "Ubuntu update (apt-get) downloads lot of initial data files."
date: 2012-05-24
forum: General Help
---

### Post by praveenthivari on 2012-05-24
Hello,

I have following problem.

Whenever I refresh update manager or run apt-get update a lot around 6-7 MB of data is downloaded, no matter how frequent I refresh it. Even if I press refresh immediately after an refresh it still downloads all those files again. 

In Earlier version of Ubuntu I didn't have this once I refresh the software database further refrsh would download data in terms of KB, but this time around it download whole database everytime I do a refresh. 
The culprit appears to be universe and extra repos.

This eats away my data. 

Any Idea of what am I missing this time?

---

### Post by praveenthivari on 2012-05-27
Anyone?

---

### Post by miasmablk on 2012-05-27
try 

```
sudo apt-get clean
```

---

### Post by Shadius on 2012-05-27
> **praveenthivari said:**
> Hello,

I have following problem.

Whenever I refresh update manager or run apt-get update a lot around 6-7 MB of data is downloaded, no matter how frequent I refresh it. Even if I press refresh immediately after an refresh it still downloads all those files again. 

In Earlier version of Ubuntu I didn't have this once I refresh the software database further refrsh would download data in terms of KB, but this time around it download whole database everytime I do a refresh. 
The culprit appears to be universe and extra repos.

This eats away my data. 

Any Idea of what am I missing this time?

Could it have something to do with "Source code" being checked in the Software Sources?

---

### Post by vasa1 on 2012-05-27
> **praveenthivari said:**
> Anyone?

I've been whining about this but I've given up now ;)

---

### Post by vasa1 on 2012-05-27
> **Shadius said:**
> Could it have something to do with "Source code" being checked in the Software Sources?
No, it doesn't.

---

### Post by Shadius on 2012-05-27
> **vasa1 said:**
> No, it doesn't.

Oh okay, just a thought. I've seen this issue in another thread, but I don't have the link. :( I think they were able to solve it. Search the forum and you might find it. Good luck.

---

### Post by vasa1 on 2012-05-27
> **Shadius said:**
> Oh okay, just a thought. I've seen this issue in another thread, but I don't have the link. :( I think they were able to solve it. Search the forum and you might find it. Good luck.
AFAICT, the problem still exists:
[http://askubuntu.com/questions/127522/why-are-my-apt-get-update-fetches-so-large](http://askubuntu.com/questions/127522/why-are-my-apt-get-update-fetches-so-large)
[http://askubuntu.com/questions/135818/the-size-of-apt-get-update-lists-is-too-big](http://askubuntu.com/questions/135818/the-size-of-apt-get-update-lists-is-too-big)
[https://bugs.launchpad.net/launchpad/+bug/1001780](https://bugs.launchpad.net/launchpad/+bug/1001780)

There are at least two threads in this forum on the topic as well.
[http://ubuntuforums.org/showthread.php?t=1966598](http://ubuntuforums.org/showthread.php?t=1966598)
[http://ubuntuforums.org/showthread.php?t=1972335](http://ubuntuforums.org/showthread.php?t=1972335)




Some workarounds have been suggested but they are workarounds.

---

### Post by Ghost_Mazal on 2012-05-27
Yeah this hurt my bandwidth so much that I changed from "daily" to "Weekly" on update checks.

---

