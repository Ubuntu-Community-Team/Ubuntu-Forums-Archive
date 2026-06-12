---
title: "_Real_ 9.04 Upstart Sequence????"
date: 2009-12-28
forum: General Help
---

### Post by huffcs on 2009-12-28
<rant>I have been trying for hours to figure out the _real_ sequence of events after the initrd process completes that get all the standard services and daemons started and all I get is a mish-mash of glop.  Even the ubuntu on-line man-pages are inconsistent in answering how 9.04 gets everything started. </rant> ;)

Now, how does the system finish getting started?  Does initrd hand off to init (or upstart?, or ???) and what does it do by default?  Please don't just tell me it runs the stuff in /etc/event.d since, taken literally, that would mean it sumultaneously enters all run-states, shuts the system down, runs the last-good-boot, and runs the sulogin binary during "single-user" mode!  _I don't think so_!

I expect that there is a missing detail that defines what the default action(s) are which I have been unable to find.  Please help.  I want to understand!

Craig.

---

