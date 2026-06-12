---
title: "newest transmission package broken"
date: 2010-07-21
forum: General Help
---

### Post by duane-tech on 2010-07-21
The most recent upgrade for transmission has broken the package.
I think it is a dependancy error between transmission-cli and transmission-gtk requiring a different version of transmission-common than what's available.
I have Kubuntu 8.04. Here's my output:

$ apt-get install transmission
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  transmission: Depends: transmission-cli (>= 2.03-0ubuntu1.08.04.1) but it is not going to be installed
                Depends: transmission-gtk (>= 2.03-0ubuntu1.08.04.1) but it is not going to be installed
E: Broken packages

---

### Post by Sonsum on 2010-07-21
did you try running ```
sudo aptitude install transmission
```?

aptitude usually has better dependency resolution

---

### Post by duane-tech on 2010-07-22
Nope, I first used adept, then when that didn't work, went to the command-line option.

I'm not sure what I did to get things working.
Of course, I tried purging all the relevant packages, and reinstalling them, also specifying the version (transmission-cli=2.xx...).
It may have been just a repository update that cleared the problem.
Whatever, everything's good now. Thanks for the suggestion, it'll go in my solution notes.

---

