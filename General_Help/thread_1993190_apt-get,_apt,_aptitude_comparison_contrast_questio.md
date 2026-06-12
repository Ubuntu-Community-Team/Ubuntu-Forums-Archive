---
title: "apt-get, apt, aptitude comparison contrast questions"
date: 2012-06-01
forum: General Help
---

### Post by charleswb on 2012-06-01
Apt-get comes with Ubuntu. I get that.

There are also some 3rd party programs that do similar things.

Is Apt (AptUrl) a 3rd party app? Is it worth installing? If so, why?

Is Aptitude a 3rd party app? Is it worth installing? If so, why?

What are differences between Apt-get, Apt (AptUrl), and Aptitude?

---

### Post by Paqman on 2012-06-01
Apturl is a tool that allows you to click on links like this: [install me]("apt:notarealpackage"). I can't remember if it's installed by default these days and I'm not on an Ubuntu machine right now. Basically if you click the link above and Software Centre opens, it's installed.

What you refer to as apt-get is actually called APT. Apt-get is one of APT's commands.

Aptitude is an alternative to APT. Both are front-ends for dpkg, which is the Debian package manager. They both do largely the same thing. Aptitude is slightly better for servers as it has a more full-featured interface on the command line, which is why it's preinstalled on the server version, but the desktop version just has APT. The desktop used to have both too, but it was decided that it's a bit pointless to have two very similar programs that do the same thing.

---

### Post by Cheesemill on 2012-06-01
I use aptitude instead of apt-get on all my machines because I find it resolves dependency conflicts more gracefully. It also automatically removes unneeded dependencies when you remove a package.

---

### Post by BBQdave on 2012-06-01
> **Paqman said:**
> Aptitude is an alternative to APT. Both are front-ends for dpkg, which is the Debian package manager. They both do largely the same thing. Aptitude is slightly better for servers as it has a more full-featured interface on the command line, which is why it's preinstalled on the server version, but the desktop version just has APT.

I like [Synaptic]("http://www.nongnu.org/synaptic/") (GUI for APT) to manage packages :)

---

### Post by Paqman on 2012-06-01
> **BBQdave said:**
> I like [Synaptic]("http://www.nongnu.org/synaptic/") (GUI for APT) to manage packages :)

Me too.

Ubuntu has a ton of tools available, such as:
[LIST]
[*]APT
[*]Aptitude
[*]Synaptic
[*]Update Manager
[*]Ubuntu Software Centre
[/LIST]

They all use the same underlying package manager to do their thing. So changes made in one are understood by all the others. Use whatever you like best, or whatever matches the job you're doing. They all have their uses.

---

