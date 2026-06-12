---
title: "Tracking publishing problem cross browser"
date: 2011-07-09
forum: General Help
---

### Post by fairflow on 2011-07-09
I'm having an issue with publishing a wordpress blog which I don't understand.  Using meerkat.  The blog is hosted by wordpress, this isn't a wordpress installation issue, it is far more basic.

Symptom: when publishing a blog on wordpress.com, nothing happens.  Eventually we get a php timeoout from the server (sometimes Firefox asks what to do with the .php file). But it is possible to save drafts.  No error messages appear anywhere and nothing happens until the timeout, prompt to deal with the php file or the page is reloaded and stopped.

Similar errors appear when accessing webmail: the remote server hangs when replying to messages.

The blog can be used as normal from other machines and it isn't a browser-specific problem (at least the same behaviour happens with chrome and firefox).  The issue also appears with blogs hosted with other servers.

It seems to be an authentication problem but the lack of error messages makes it hard to know where to begin to trace it.  I've looked at auth.log but don't see any entries that coincide with the occurrence of the problem. Which log files should we search, or has anyone else experienced this problem?

The only thing that might have caused an issue is that I upgraded from an early version of Ubuntu to 9 and then to 10, in the hope that it would fix the problem. But upgrading doesn't change the problem.

About me: I'm managing an Ubuntu installation for a friend.  I'm generally experienced with Unix/Linux but don't know how to go about tracing the source of this problem.

---

