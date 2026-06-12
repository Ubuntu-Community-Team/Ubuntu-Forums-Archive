---
title: "Apps for Linux"
date: 2011-07-23
forum: General Help
---

### Post by Bernard43 on 2011-07-23
Can anyone tell me if apps written for Linux are valid for all Linux variants?
The reason I ask is that I have used RealBasic to write my own Windows software and if I change to Ubuntu will have to consider converting.

---

### Post by JKyleOKC on 2011-07-23
The only accurate answer to your question is "Maybe." It depends on whether the app includes distribution-specific features.

For instance, RedHat and its relatives use one plan for organizing the configuration directory, while Debian and its offspring use another. If the app includes only one of these approaches, it won't work on any distribution that uses the other.

It's possible to determine which is present, in this case, and then switch the code appropriately -- but it's even better to avoid such problems in the first place by steering clear of all distribution-specific features.

Unfortunately, the only way to be sure that you've done so is to test the app on all the different distros that you can. Using virtual machines makes this possible, but unless you're planning to distribute your apps to others, there's really no need to be concerned with the question at all. Just make it work on the distribution you're using!

If we restrict the question in this way, then the answer is "Probably yes." All the distributions use the same underlying kernel, but may have different libraries. If you're downloading packages, stick to the repositories for whichever distro you prefer rather than searching the web. If you're rolling your own, use the tools provided in the repositories. They will be tailored to the distro you use, and should take care of almost all the possible compatibility problems.

---

### Post by coldraven on 2011-07-23
I don't know if this will work for you but you could look at "alien", it's in the Synaptic Package manager. The description is below:

> Alien allows you to convert LSB, Red Hat, Stampede and Slackware Packages
into Debian packages, which can be installed with dpkg.
It can also generate packages of any of the other formats.
This is a tool only suitable for binary packages.

---

### Post by sanderd17 on 2011-07-23
It's always possible to make something that is OS specific or distro specific, but some languages hammer on the fact that they are OS independant. Like Java or scripting languages like Python or Ruby.

So yes, the only correct answer is "maybe", but you can make something distro independent with almost any popular language. Some languages do ask more effort.

---

### Post by Bernard43 on 2011-07-23
Thanks for the answers folks, you have given me all I need.

---

