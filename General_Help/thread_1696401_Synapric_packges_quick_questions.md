---
title: "Synapric packges: quick questions"
date: 2011-02-27
forum: General Help
---

### Post by Beowolf64 on 2011-02-27
Hello everyone.
Need your input to clarify few things. Your input is greatly appreciated.

There are several package types in synaptic.

**-doc.** Obviously, these are docs. They go into */usr/share/doc* folder. Is there some sort of GUI for viewing and searching docs, something like MSDN?

**-dev.** Not exactly sure about these ones. Are these development files (binaries, source code etc) for coders/developers who want to work on that particular project?

**-dbg**. Not sure about these ones too. Debug versions of binaries? Shouldn't they be included with development files?

Let's be more specific. 

**libstdc++6**. This has runtime for applications compiled with C++.
**libstdc++6-4.5-dev.** Needed to develop and compile those applications.
**libstdc++6-4.5-dbg. **Needed to debug applications which use binaries from **libstdc++6.** 

Is that right? Please feel free to point out if I got something wrong. Thank you.

---

### Post by Silent Warrior on 2011-02-27
-doc-question: Sure! man [name-of-app/utility/whatever], gedit, OpenOffice, kwrite, leafpad, [trails off into infinity]... Well, you get the idea. Make it easy for yourself and just open the folder in Nautilus and double-click the documentation-file and see what loads up.

-dev: Most commonly headers, I think. Either that or source code. Most useful for developers, yes, but if you're going to do any compilation on your own (Gtk theme-engines, panel-applets) you'll need some -dev packages. Just don't install them if you aren't sure you'll need them. (I think they bloat stupendously, though I could be mistaken. They might not be very large, but their size when extracted can come as a shock.)

-dbg: Binaries with debug-extensions, as far as my understanding goes. I believe their purpose is to improve accuracy of bug-reporting and -fixing. Normally you have no reason at all to use -dbg packages. I think most say that you shouldn't install these unless instructed. The installed binaries might even be more than twice the size of the normal versions...

Your example with libstdc++ looks quite correct to me, though the -dbg-thing might possibly be better explained. But all correct, in a binary sense.

---

### Post by Beowolf64 on 2011-02-27
Aren't **-dbg** packages for those who want to debug but doesn't want to compile all binaries their application links to?

And yes, debug packages are huge. My Linux installation is 10 gig already, even though I don't have any video/audio files. But it is still much smaller than space used by Window development tools.

There are also **-source** packages. How they differ from **-dev** ones?

---

### Post by Silent Warrior on 2011-02-27
Debugging: *Shrug* I suppose. Never done it myself, though.

-source... I would assume they're pure source-code - headers, .c/.cpp-files, everything - for the given package. -dev-packages seem to mostly mention headers (unless they contain some binaries as well).

I'm not really familiar with this part of packaging, though. Well, not really familiar with packaging AT ALL, I should say, but -dev/-source is a mystery I never bothered looking that deep into.

---

### Post by Beowolf64 on 2011-03-05
SOLVED.[B]
dbg[/B] is for developers. These provide debug symbols for the respective package. **dbg'**s can be compiled from the corresponding **dev** packages.

---

