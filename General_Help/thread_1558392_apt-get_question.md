---
title: "apt-get question"
date: 2010-08-22
forum: General Help
---

### Post by bprins on 2010-08-22
Hi,

Probably a dumb question, but can't find my answer elsewhere.

I am more a 'terminal-apt-get-fan' then an 'update-manager-fan'. The only thing I don't know how to do, is get a list of proposed updates after sudo apt-get-update, like the update manager shows me after I pressed the "check" button.

Now I bet there is a way, I just can't find it :).

Thanks in advance.

Bas

---

### Post by scorp123 on 2010-08-22
```
sudo apt-get --simulate dist-upgrade
```

---

### Post by Dalek Draco ON LINUX on 2010-08-22
Above post is the answer.

---

### Post by bprins on 2010-08-22
Found something that works for me.

Apparently apt-get is out and aptitude is in.

Read a nice article about it here for those who would like to read:
[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

---

### Post by bprins on 2010-08-22
Thanks for the replies, read them just now.

So it is possible with apt-get as well. 

Bas

---

### Post by WorMzy on 2010-08-22
> **bprins said:**
> Found something that works for me.

Apparently apt-get is out and aptitude is in.

Read a nice article about it here for those who would like to read:
[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

[As of 10.10, aptitude isn't going to be installed by default (it'll still be in the repos though)]("http://www.webupd8.org/2010/06/aptitude-removed-from-ubuntu-1010.html")

---

### Post by bprins on 2010-08-22
Lol that's strange to read after the many many sites that were totally pro-aptitude :-)

But as long its in the repositories I'll give it a shot.

---

### Post by scorp123 on 2010-08-22
> **bprins said:**
> Lol that's strange to read after the many many sites that were totally pro-aptitude :-)

The original reason for *"pro aptitude, against apt-get"* was that older versions of "apt" were not able to keep track of dependencies in the same way "aptitude" was, at least back then.

Example:

You install a package "foo" with ***sudo apt-get install foo***, and it wants to pull in the packages "bar1", "bar2", and "bar3" as well. With the old versions of "apt" it then happened that when you removed "foo" again (***sudo apt-get remove foo***), it simply forgot to remove "bar1", "bar2" and "bar3" again. Result: You end up having useless packages in your OS.

The "pro aptitude" argument then was that ***"sudo aptitude install foo"*** would deliver the same result as above (= install the package), but "aptitude" would then keep track what dependencies it pulled in too. Result: When you remove the 'foo' package again, "aptitude" would remember that it also has to remove the "bar-xyz" packages as well.

**Nowadays "aptitude" doesn't have that advantage anymore.**

You can simply tell "apt" to search for unneeded packages:
```
sudo apt-get autoremove
```

Result: "apt-get" will scan your OS for no longer needed dependencies that it might have pulled in earlier.

Not that you would have to use that command so often, because "apt" has been greately improved and should now be able to keep track of stuff that it pulled in as dependencies ...

All in all there is no real need for "aptitude" anymore, it no longer offers any significant advantage over "apt-get". Hence why it won't be there anymore by default on Ubuntu 10.10 ... there is no need anymore. But of course: those used to it are still free to install it if they wish ... 

So that's the entire story.  :D

---

