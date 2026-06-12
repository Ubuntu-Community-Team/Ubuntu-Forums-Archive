---
title: "How do you run a C# script in Ubuntu?"
date: 2010-12-19
forum: General Help
---

### Post by abelundercity on 2010-12-19
I'm running a standalone OpenSimulator grid with an eye toward making some machinima.  In that vein I'd like to create some unmanned avatars, or "bots," to act as extras.

I came across <a href="http://opensimulator.org/wiki/Building_a_bot">this C# script</a> that seems to meet my needs, but I have no idea how to proceed with it.  I've got it saved as a text file on my drive, but I'm uncertain as to what to do next.

Any input for this would be appreciated.

---

### Post by x1a4 on 2010-12-19
Hi,

C# is not a scripting language.  It is Microsoft's object-oriented programming language derived from C used in its .NET platform.  You have to compile it before you can use it.  To compile it you need Windows and a C# compiler/IDE such as MS Visual Studio.  Although it *_might_* be possible to compile it on Linux.  Google for it.

EDIT: I just looked at opensimulator.org and it appears that the scripting engine does allow C# as if it were a script (The example you provided is not one of those) albeit it's a bit of a "black art".  Have a look at the [Scripting Documentation]("http://opensimulator.org/wiki/Scripting_Documentation") for more information.

---

