---
title: "Whut ?"
date: 2010-05-14
forum: General Help
---

### Post by Swagman on 2010-05-14
[img]http://www.upload3r.com/serve/140510/1273839083.jpeg[/img]


Wicked Message !!

Who nicked the update repos ?

---

### Post by Bachstelze on 2010-05-14
Obvious 'shop is obvious, but thanks for trying. :)

---

### Post by Swagman on 2010-05-14
Why would I "shop" that ?

I'd "GIMP" it anyway !!

---

### Post by Old Marcus on 2010-05-14
This is real, I've seen other people have this error as well.

---

### Post by praveenthivari on 2010-05-14
I too got tht msg. Solution is just go Software sources and in repos tick on ubuntu archieves source and reload

---

### Post by McRat on 2010-05-14
Yup.  I like it!

Much better than:

"Next time you need to exit Windows, please uses the shutdown button.   If you believe it was OUR fault, you are WRONG!!!  HAHAHAHA!!!"

---

### Post by Penguin Guy on 2010-05-14
Looks like there's no easy fix - you may have to reinstall. See [previous Ubuntu Forums post]("http://ubuntuforums.org/showthread.php?t=1466944") and [official bug report]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886").

---

### Post by yeagdeeds on 2010-05-14
Neither messing with the repositories or reinstalling seem to make any difference...Unless all third party repositories are removed. The error is very erratic. It does not seem to matter which third party it is. I am using Kubuntu 10.04 x64 with all updates. This is a new install as of about 10:00am est. I have also confirmed the bug in Ubuntu 10.04 x64.

---

### Post by chillicampari on 2010-05-14
> **Penguin Guy said:**
> Looks like there's no easy fix - you may have to reinstall. See [previous Ubuntu Forums post]("http://ubuntuforums.org/showthread.php?t=1466944") and [official bug report]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886").

Reinstalling is not the solution and shouldn't be recommended, it looks like the problem will just be reintroduced with adding third-party repositories. 

***

In the meantime, going off yeagdeeds and others info from here and the bug report, it might be a good idea to comment out or untick user added/third party repositories for now and subscribe to the bug on launchpad.

Edit- I'm flagging this post for a thread move request to a better section of the forum, since it's turned into a support/bug discussion.

---

### Post by cariboo on 2010-05-14
Moved to general Help, by request.

---

### Post by chillicampari on 2010-05-14
Thanks cariboo907! I know this is Swagman's thread, but would it be possible to update the thread title to reflect the error in it so people having the same problem will find it easier? Like "Something wicked happened resolving (the repositories)" or something like that? Thanks again!

---

### Post by southernman on 2010-08-18
Removing the source for a third party software seems to have solved this issue for me. Time will tell though. Cherokee Server was the third party source in my case.

---

