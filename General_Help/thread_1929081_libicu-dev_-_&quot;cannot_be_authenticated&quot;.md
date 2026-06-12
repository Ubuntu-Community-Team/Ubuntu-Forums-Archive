---
title: "libicu-dev - &quot;cannot be authenticated&quot;"
date: 2012-02-21
forum: General Help
---

### Post by Matt M on 2012-02-21
[solved] - sudo apt-get update seems to have done the trick.

I'm a beginner programmer experimenting with Haskell. For a new project, I'm thinking of installing the Haskell text-icu package. 

When I attempt to do so, I get the message: 

[INDENT]cabal: Missing dependencies on foreign libraries:
* Missing C libraries: icui18n, icudata, icuuc
This problem can usually be solved by installing the system packages that provide these libraries (you may need the "-dev" versions).[/INDENT]

OK, so after checking with Synaptic, it seems like installing libicu-dev is the way to go, since libicu-44 is already installed on my system.

However, when I try to install it, I get the message: 

[INDENT]WARNING: The following packages cannot be authenticated!
  libicu-dev[/INDENT]

That's a bit concerning, both in terms of my own computer's security, and in terms of security and ease of installation for anyone else trying to install my program (if I ever get it finished).

Can anyone offer some advice about this package and whether I should go ahead and install it?

---

