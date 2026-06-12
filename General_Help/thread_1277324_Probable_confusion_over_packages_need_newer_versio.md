---
title: "Probable confusion over packages: need newer version of Git"
date: 2009-09-28
forum: General Help
---

### Post by tom82 on 2009-09-28
Hi all,

This will probably be a total 'n00b' question, but I've tried searching for the answer myself and keep drawing a blank:

I'm confused as to how I can get up to date versions of software by using aptitude / Synaptic Package Manager.  In this instance, I'm trying to get a more recent version of git.

I've done a 'sudo aptitude update', and check the latest version of the git-core package is still listed as 1:1.6.0-4-1ubuntu2.  The latest version of git is at least 1.6.4, so this is pretty old.  What packages / repositories do I have to point to to get more recent versions of packaged software??

Thanks for your help,

Tom

---

### Post by wojox on 2009-09-28
If that's what's in the repo's than it's your only choice besides downloading from the site:

[http://git-scm.com/](http://git-scm.com/)

---

### Post by tom82 on 2009-09-28
Oh really?  I remember back from when I used to run Gentoo that there was a concept of development sources that you could opt to use, which generally meant to mean you could pull down up to date versions of software packages.  Is there no equivalent system in Ubuntu?  Or is it just meant to be a more 'stable' platform than Gentoo?

Thanks,
Tom

---

### Post by Moop on 2009-09-28
Have you tried looking for a ppa that has a updated version?

[https://launchpad.net/~git-core/+archive/ppa]("https://launchpad.net/%7Egit-core/+archive/ppa")

---

### Post by t0p on 2009-09-28
> **tom82 said:**
> Oh really?  I remember back from when I used to run Gentoo that there was a concept of development sources that you could opt to use, which generally meant to mean you could pull down up to date versions of software packages.  Is there no equivalent system in Ubuntu?


If the developers of the software in question have created a repository for newer/development versions (known as a PPA), then you can add this PPA to your Software Sources list (at /etc/apt/sources.list). More on how to do that is [here]("https://help.ubuntu.com/community/Repositories/CommandLine").  You'll need to look at the developer's site to see if they have a PPA.  The details you'll need to add to your Sources List file will also be on their site.

If the devs don't have a repository for their new versions, you will probably have to download the latest packages from their website and install them yourself.  If the packages are in .deb format, installation is pretty easy - you need to right-click on the package and select to install with gDebi.  If the package comes as source code inside a tarred archive (with file extension ".tar.gz" for instance), it's a bit more complicated.  Information on how to compile source code can be found [here]("https://help.ubuntu.com/community/CompilingEasyHowTo").

In all events, you will need to go to the developer's website first of all, to find the details you need.  Remember, it's the developers who are responsible for their new or development versions, not Ubuntu.

---

### Post by tom82 on 2009-09-28
Thanks guys, that's a big help.

So PPAs are the missing piece of the puzzle..  I get it now!  :-)

Found a git PPA [here]("https://launchpad.net/~git-core/+archive/ppa"), seems to have worked a treat.

---

