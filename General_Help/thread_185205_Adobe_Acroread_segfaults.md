---
title: "Adobe Acroread segfaults"
date: 2006-05-31
forum: General Help
---

### Post by neumayr on 2006-05-31
Hi,
I'm having problems getting acroread to work.
After I couldn't find an acroread package on kubuntu 6.06, I installed it from Adobe's website. Problem is, it segfaults. An 'strace acroread' suggested it couldn't find libscim and libscim-x11utils (why would it need those?), so I symlinked them to acroread's lib directory.
Now it finds both libraries, but still segfaults - and I'm out of ideas.

Does anyone here have an idea on what's wrong? I'll attach the compressed strace output to this post, just in case..

-neumayr

---

### Post by uteck on 2006-05-31
There are a few dependencies that are missing, but I can't remember what they are. You could using Automatix to install it.  It should solve the dependency problems.
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by asimon on 2006-05-31
Actually Acrobat Reader is packaged for Kubuntu in the multiverse repository (which is not enabled by default), the package is called [acroread](http://packages.ubuntu.com/dapper/text/acroread) and the mozilla plugin [acroread-plugins](http://packages.ubuntu.com/dapper/text/acroread-plugins).

For instructions on how to enable the multiverse repository see the [Adding Repositories Howto](https://wiki.ubuntu.com/AddingRepositoriesHowto).

... or use what uteck recommended, Automatix. Never used that but it should be able to help installing acroread and such stuff too.

---

