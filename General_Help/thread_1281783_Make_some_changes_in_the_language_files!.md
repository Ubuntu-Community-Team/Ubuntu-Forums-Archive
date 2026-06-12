---
title: "Make some changes in the language files!?"
date: 2009-10-03
forum: General Help
---

### Post by artheus on 2009-10-03
Hi!

I'm trying to customize my Ubuntu 9.04, and I want to make some changes to some of the words and sentences around Ubuntu.

What I want is not to translate the Ubuntu, I know of the Launchpad option and stuff.. What I want is to customize the text around Ubuntu 9.04, just for my own installation of Ubuntu. Is there a simple way to do this?
Or do I have to do it some hard way, like downloading source, and stuff!?

Would really like an answer for this :)

Cheers,
Artheus

---

### Post by kayvortex on 2009-10-03
I don't know for sure, but I'd imagine that the text dialogue is hard-coded into the specific program; so, I'd guess that you'd have to do it the hard way!

Edit: actually, maybe you can: I downloaded a language-pack package source file and took a look at it. It seems to contain the translation text in .po files (which I'd imagine are "object files" in plain text that are dynamically linked to the specific program). Some wikipedia info (!) is located [here]("http://en.wikipedia.org/wiki/Gettext"), and it *looks* like you can just install the language pack and change the specific translation text. I'd look into how the actual translation stuff is done in Ubuntu/GNOME to be sure (i.e. do some googling!), but I think it might be possible.

---

