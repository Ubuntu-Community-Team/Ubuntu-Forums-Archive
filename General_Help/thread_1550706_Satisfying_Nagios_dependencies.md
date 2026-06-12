---
title: "Satisfying Nagios dependencies"
date: 2010-08-11
forum: General Help
---

### Post by Karl1982 on 2010-08-11
I have installed Nagios a number of different ways in the past year, mostly in test environments, but we do have a production Ubuntu 10.04 Nagios server in our office in which I compiled and installed Nagios from source and followed it with Centreon.  It's a long process... and I would use something like Opsview, but I haven't decided if I can get used to its interface yet.  Anyway, that's beside the point.

What I'm wondering is if there's an easier way to install Nagios from source but satisfying its dependencies through, say... a repository metapackage or something.  The problem I ran into installing nagios3 via apt was that it puts everything in different places than if I compile it from source, so then if I turn around and install Centreon on top of it, I have to change... every... folder... that Centreon uses.  By default, it matches the layout of Nagios installed from source.  But if I do that, I have a long list of plugin dependencies, and I still don't think I've met all their requirements.

So anyway, I was wondering if someone knows how to get the best of both worlds there.  The reason being, we're looking into possibly installing a Nagios virtual server at additional remote sites, and I'm trying to lighten my workload if possible.  Being able to satisfy all the source's dependencies up front would greatly simplify the following Centreon installation.  **So, my real question is this: Is there some way to install all the dependencies of Nagios via apt, but without Nagios itself so it and its plugins and NDOutil can be installed from the latest source from [www.nagios.org]("http://www.nagios.org") afterward, and be clear of any package dependency issues?**

---

### Post by jlanawalt on 2010-08-11
You can look at the dependencies of nagios and install those by hand, or create your own metapackage that depends on the same things nagios depends on, but that doesn't fix your source version path and general compile effort duplication issues. 

Where are the results of your build+install process are going, to /usr, /usr/local or /opt? I'm very wary of mixing non-packaged stuff with packaged stuff to /usr.

I think the right thing to do is to package your own from-source build of nagios with the paths and dependencies adjusted to play nicely as a drop-in replacement for the one from Ubuntu, and to do the same with Centreon. Fix all those paths once (for a given version/build) and install from packages, not from source. Even better would be to find packages from someone already doing this.

---

### Post by Karl1982 on 2010-08-15
That sounds like a very good idea, making my own packages with all the necessary changes built in.  I wish I had some earthly idea of how to do it.  I seem to do everything in the IT industry EXCEPT programming, so I'm not sure I'd be able to modify source code correctly.

If I remember correctly, the from-source builds are going to /usr/local/.  Although... you know, I really don't care that much where they end up so long as everything's good and it doesn't make a big mess.  Maybe if I could make a Centreon package with the paths adjusted to match the repository's nagios3, that would save me a significant amount of work because then I could just install Nagios with apt and let Centreon install with defaults afterward, provided of course Centreon's dependencies are met.  I seem to recall making a few adjustments during Centreon's installation other than pathing, but I'd have to build another Nagios server to remember what they were.

I'm still learning Ubuntu's inner workings.  How involved of a task are we talking?  I really don't build new Nagios servers that often, so I'm tempted to just let it go.  I guess it's more about the learning experience than really making my life easier.

---

