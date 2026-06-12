---
title: "maintain package"
date: 2009-08-09
forum: General Help
---

### Post by ensis2k on 2009-08-09
Hi

there is a bug, preventing pdf generation, in Ubuntu's most recent doxygen (1.5.8-1) which renders it unusable for me. The bug has been fixed in the most recent release(1.5.9). 

Now I'm asking myself if I can send a package to ubuntu and if it would be accepted???

Btw. Synaptic shows the Ubuntu icon right next to it, does it affect my intentions?

Ps:
I am aware of [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by ensis2k on 2009-08-14
Okay, so i've done an actualized package for doxygen 1.5.9. The [guide]("https://wiki.ubuntu.com/PackagingGuide/HandsOn#Tutorial%202:%20Updating%20a%20Package") was easy to understand but it is not stated what to do after:
```

sudo pbuilder build doxygen_1.5.9-0ubuntu1.dsc

```

Whom do I have to send it? Which files?

Also I'd like to know what's behind the naming convention of **0ubuntu1** after the package version.

Help? Anybody?

---

### Post by ensis2k on 2009-08-14
Okay, so for the ubuntu forums archives I will finish my monologue with an answer :)

After finishing the last step of the guide, one has to file a bug on launchpad.net and has to attach the diff. doxygen_1.5.9-0ubuntu1.diff.gz in my case.

But! Before you even try to do an update you should check if the desired version is in the latest ubuntu version. In my case my efforts were in vain because doxygen 1.5.9 was already in karmic (while the latest stable is jaunty right now). So I should have checked [https://launchpad.net/ubuntu/+source/doxygen](https://launchpad.net/ubuntu/+source/doxygen) before.

If I want to have the latest doxygen in my jaunty, then I have to ask for a Backport from karmic to jaunty. [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Cheers

y

---

