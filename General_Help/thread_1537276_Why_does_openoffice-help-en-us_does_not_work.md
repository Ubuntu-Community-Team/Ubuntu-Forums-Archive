---
title: "Why does openoffice-help-en-us does not work?"
date: 2010-07-23
forum: General Help
---

### Post by Tombgeek on 2010-07-23
Hey guys

I, along with many other users, have found a bug in OpenOffice 3.2.0 where it would take 20 seconds or more to open a file. The bug only seems to work if there is an internet connection. However, if there was none, then it would take a slit second to open a file. One user reported that the problem was solved when he downloaded the help packages for OpenOffice (he runs Kubuntu 10.04 if I am right).

Now the problem is I downloaded the help packages from the Software Centre, but I still get a message when I go to Help > OpenOffice.org Help or if I press F1.

"The help file for this topic is not installed..
Please install the openoffice.org-help-en-us package or local specific help package openoffice.org-help-<language code>."

But I installed the package, I do not see what the problem is.
Can you guys please help me out? Where can I get the packages? The only place I managed to find them was here [http://packages.debian.org/lenny-backports/openoffice.org-help-en-us](http://packages.debian.org/lenny-backports/openoffice.org-help-en-us)
But I don't know if it will work properly.

Sorry if this is a stupid question. I am still inexperienced with Linux and Ubuntu.

---

### Post by bobcollard on 2010-07-23
> **Tombgeek said:**
> Hey guys

I, along with many other users, have found a bug in OpenOffice 3.2.0 where it would take 20 seconds or more to open a file. The bug only seems to work if there is an internet connection. However, if there was none, then it would take a slit second to open a file. One user reported that the problem was solved when he downloaded the help packages for OpenOffice (he runs Kubuntu 10.04 if I am right).

Now the problem is I downloaded the help packages from the Software Centre, but I still get a message when I go to Help > OpenOffice.org Help or if I press F1.

"The help file for this topic is not installed..
Please install the openoffice.org-help-en-us package or local specific help package openoffice.org-help-<language code>."

But I installed the package, I do not see what the problem is.
Can you guys please help me out? Where can I get the packages? The only place I managed to find them was here [http://packages.debian.org/lenny-backports/openoffice.org-help-en-us](http://packages.debian.org/lenny-backports/openoffice.org-help-en-us)
But I don't know if it will work properly.

Sorry if this is a stupid question. I am still inexperienced with Linux and Ubuntu.
How did you install it?  I just installed mine using Terminal and the following code whcih works.
```
sudo aptitude install openoffice.org-help-en-us
```

---

### Post by CoolJohnB on 2010-07-23
I have the help files installed on mine, but it makes no difference it still takes 20+ secs to load a file when connected to the Internet, but instantly when not connected!

Does anyone know a solution for this?

---

### Post by Tombgeek on 2010-07-24
> **bobcollard said:**
> How did you install it?  I just installed mine using Terminal and the following code whcih works.
```
sudo aptitude install openoffice.org-help-en-us
```

I installed it through the Ubuntu Software Centre

> **CoolJohnB said:**
> I have the help files installed on mine, but it makes no difference it still takes 20+ secs to load a file when connected to the Internet, but instantly when not connected!

Does anyone know a solution for this?

I reported the bug to OpenOffice.org, and so far they have found clues as to what causes it, but they have not found a solution.

Here is the Issue Report:
[http://qa.openoffice.org/issues/show_bug.cgi?id=112546](http://qa.openoffice.org/issues/show_bug.cgi?id=112546)

---

### Post by Hagar Delest on 2010-07-26
I don't remember having seen a fix to the help file problem. Switch to the Sun version, it doesn't have the problem: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

