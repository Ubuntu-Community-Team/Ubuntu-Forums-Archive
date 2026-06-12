---
title: "where does ubuntu want its files?"
date: 2009-10-05
forum: General Help
---

### Post by markseger on 2009-10-05
I'm trying to build my first package and am making progress but once again I'm stumped with the messages debuild is generating.  Now it's telling me it doesn't like the directories my code is in but doesn't tell me what directory it wants to see it in.  Many of these messages are warnings which quite frankly I'm going to ignore - why should it care if there's no man page associated with a ph file?  But some are errors and while I can't ignore those I have no idea what's wrong.

For example, it's tell me I several non-standard top level dir named docs/, man1/, util/ and etc.  The directory structure I'm using is one in which I put my code into subdirectories under /opt/hp/collectl and then put links in the standard locations to point to them.  This way my entire package lives under a single directory instead of being spread around the system.  It also makes it real easy to have multiple instances on the same system which makes devlopment/testing much easier.

So I guess the question becomes where does Ubuntu want me to put them and is there a way to tell it not to worry because the links are in the right place?

There is also one other error that reads "file in etc not marked as conffile". Any clue what this means?

Getting back to all those warnings, is there a way to get then to stop?  For example, in my docs/ directory I have a bunch of html, jpg and css.  I also have some utility scripts in util/, which it doesn't like either.  There are others as well, but I think this gets my point across.

Can anyone shed any light on this and/or how to make things work without having to go through too much pain?

-mark

---

