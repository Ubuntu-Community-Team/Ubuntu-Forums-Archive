---
title: "How can I update to latest Okular on Ubuntu 10.04?"
date: 2012-07-13
forum: General Help
---

### Post by El Potro on 2012-07-13
Is there any way to do this? Because the version available in the repos of 10.04 is pretty outdated, and has an annoying bar at the bottom that takes a considerable amount of space from my small netbook's screen.

This has been fixed in newer versions, but I can't install them straightforward from the official repositories.

I tried cloning and installing from git, but apparently I need to update all the KDE libraries, and that sounds kinda impossible on Ubuntu 10.04. Does anybody know how to do it?

Is it there any alternative way?

Thank you very much in advance

---

### Post by El Potro on 2012-07-14
bump

---

### Post by holycow131415 on 2012-07-15
Google fail?

[http://askubuntu.com/questions/120996/how-do-i-install-the-latest-version-of-okular](http://askubuntu.com/questions/120996/how-do-i-install-the-latest-version-of-okular)

Explains it all towards the bottom.

---

### Post by El Potro on 2012-07-15
Hello

sorry but this link is of no help. I need a solution, and there only says something like "install Ubuntu 12.04" which I want to avoid.

Isn't there anybody out there that could install the latest Okular version on Ubuntu 10.04?

I tried a work-around, installing last version from Okular for Windows, and running it through wine, but it crashes.

Anybody can help me with Okular?

thank you very much

---

### Post by Cheesemill on 2012-07-15
I don't think that it's possible.

The latest Okular has KDE dependancies that aren't available for 10.04.
Your only option really is to upgrade Ubuntu to a later release.

---

### Post by El Potro on 2012-07-16
Hi there people!

I'm very happy because I just finished compiling the same version of Okular I was using (0.10.5) but with a patch applied that lets me hide the annoying space consuming bottom bar. This was the feature I was needing.

Basically what I did was fetching the source of the package kdegraphics from debian squeeze and applying this patch [https://bugs.kde.org/attachment.cgi?id=23451]("https://bugs.kde.org/attachment.cgi?id=23451"), which needed a little of hand patching too, because some lines didn't get patched because of an error. Then compiled, installed, and that's it! easy peasy lemon squeeze!

How could I share this with the rest of you? Because even though this distribution is "old", I believe that more than one person is going to find what I did useful.

If there are no further suggestions you can always try to contact me and I'll gladly help, also I'll write an article about this in the blog of my signature. :popcorn:

---

