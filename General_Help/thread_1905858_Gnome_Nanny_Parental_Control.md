---
title: "Gnome Nanny Parental Control"
date: 2012-01-07
forum: General Help
---

### Post by cousew on 2012-01-07
I have installed gnome nanny parental control from the Ubuntu Software Center. When I launch the program it prompts for the administrative which I enter. Then the program never loads. I am on UBUNTU 11.10 with a Compaq Presario 2500. I am new to Linux so any help is appreciated. Thanks.

---

### Post by jerrrys on 2012-01-09
The reviews in the software center say it don't work in 11.10, yet.  There is a transformation going on right now from gnome2 to gnome3 and not all packages will work in 11.10.....yet

[ATTACH]210509[/ATTACH]

---

### Post by cousew on 2012-01-11
Are there any other alternatives that work in 11.10

---

### Post by Guido Tabbernuk on 2012-01-22
> **cousew said:**
> Are there any other alternatives that work in 11.10
I had the same problem and I ended up getting Nanny development version from GIT repository and fixing it for myself. Since I don't use web filtering I didn't care much about that (however, it seems to work). I also didn't care about indicator icon and blocking other things besides user session. Neither of them seems to work (but probably is not too hard to fix). I implemented a chores system which makes it possible for user to contract a chore and get rewarded extra computer time for that.

You can install and try it from: [https://launchpad.net/~boamaod/+archive/nanny-test](https://launchpad.net/~boamaod/+archive/nanny-test)

Feedback is welcome, but I don't plan to implement/fix things I don't use myself. I encourage you to do it yourselves, of course.

---

