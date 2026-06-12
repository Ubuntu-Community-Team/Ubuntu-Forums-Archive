---
title: "Is LD_LIBRARY_PATH &quot;special&quot; &amp; what is the &quot;right &quot; way to set environment, etc.?"
date: 2010-05-04
forum: General Help
---

### Post by cosmicaug on 2010-05-04
Hi,

        I just installed a bunch of software on a Ubuntu Karmic Koala Desktop installation and got everything to work (it's a VM but that is not important). One of the items was ccp4, a x-ray crystallography suite. Before executing the front-end from the a terminal (I'm using Bash), various things have to be set up by sourcing two scripts, ccp4.setup & ccp4-others.setup the ccp4-others.setup script sets up or modifies three variables, PATH, LD_LIBRARY_PATH & MANPATH.

        I wanted to arrange it so that you don't have to enter commands manually so I tried to set it up so that the two scripts would execute on startup. To this end, I modified .profile so that the last line calls a file where I would do all the set up work.

So the last line of .profile was as follows:
```
# Call init.sh to set things up nicely for various programs.
. ~/.init.sh
```And .init.sh was as follows:
```
# This should be called from ~/.profile .
# It will be used to set up various programs (environment, etc).

# Sets up environment for Phenix.
# Note that a "." separated by white space is equivalent to "source" in csh.
. /usr/local/phenix-1.6.1-357/phenix_env.sh

# Set up ccp4
. /usr/local/ccp4/setup-scripts/sh/ccp4.setup
. /usr/local/ccp4/setup-scripts/sh/ccp4-others.setup
```So far so good.

Then I upgraded to Lucid Lynx.

What I found is that the ccp4 front-end would no longer work.

I tried reinstalling ccp4 and it did not change anything. Troubleshooting revealed LD_LIBRARY_PATH not to be set even though PATH & MANPATH were properly set.

So my question is, why did this happen? is LD_LIBRARY_PATH special? Did it somehow get treated different by Lucid Lynx as compared to how Karmic Koala treated it and why was this the case?

So in the end, it appears that I fixed the problem but I am still unsatisfied because I want to know the why. What I did is call .init.sh from .bashrc instead of from .profile . Why did the call work from .bashrc & not from .profile? Why did it work OK for the PATH & MANPATH variables & not for the LD_LIBRARY_PATH variable? And finally, what would be the official Ubuntu approved way of doing what I wanted to do? Was it to put it in .bashrc like I did?

TIA,
August

---

