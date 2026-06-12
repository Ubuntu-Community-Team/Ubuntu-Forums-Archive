---
title: "Has anyone tried manual install of Banshee 1.5 on Intrepid?"
date: 2009-07-25
forum: General Help
---

### Post by brookie on 2009-07-25
Hi,

I am bored today so i wanted to install banshee 1.5 from a tarball but be able to undo/uninstall all the changes if it fails, or even if it doesn't. 

I found a cool link for an easy compiling howto here:  [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

It seems pretty straight forward but I failed miserably trying to upgrade Ryhthmbox in the past.

If I do it and it fails (which it probably will), I want to undo stuff to keep my system clean. 

...so just thought I would see if anyone else has tried it already.

By the way, Banshee 1.43 works great for me other than it hangs when fetching cover art and has to be shut down and restarted or it will hog the cpu. For now I disabled the Cover Art Fetching.

Cheers, 
brook

---

### Post by madsmeg on 2009-07-26
Before compiling from source, its allways a good idea to install the dependencies.. ```
sudo apt-get build-dep banshee
```

BUT, as you already have banshee installed, installing from source shouldnt be a problem. As for uninstalling, you could force install the banshee from the repo's over what you will be installing... I think...

---

### Post by brookie on 2009-07-26
okay, been kina busy but finally got to it and yep, failed again...

i followed the howto above and 

./configure seemed to work without any erors but make failed with this:

Making all in tests
Making all in Analyzer
  MCS   Analyzer.exe
Analyzer.cs(121,66): error CS0121: The call is ambiguous between the following methods or properties: `System.Linq.Enumerable.Min<Banshee.Tests.TestCase>(System.Collections.Generic.IEnumerable<Banshee.Tests.TestCase>, System.Func<Banshee.Tests.TestCase,double?>)' and `System.Linq.Enumerable.Min<Banshee.Tests.TestCase>(System.Collections.Generic.IEnumerable<Banshee.Tests.TestCase>, System.Func<Banshee.Tests.TestCase,double>)'
/usr/lib/mono/gac/System.Core/3.5.0.0__b77a5c561934e089/System.Core.dll (Location of the symbol related to previous error)
/usr/lib/mono/gac/System.Core/3.5.0.0__b77a5c561934e089/System.Core.dll (Location of the symbol related to previous error)

so any ideas where to go from here?

i found this on nabble but don't know how to edit the file in question for workaround:
[http://www.nabble.com/1.5.0-Error-after-%22make%22-td24011281.html]("http://www.nabble.com/1.5.0-Error-after-%22make%22-td24011281.html")

---

### Post by directhex on 2009-07-26
> **brookie said:**
> okay, been kina busy but finally got to it and yep, failed again...

i followed the howto above and 

./configure seemed to work without any erors but make failed with this:

Making all in tests
Making all in Analyzer
  MCS   Analyzer.exe
Analyzer.cs(121,66): error CS0121: The call is ambiguous between the following methods or properties: `System.Linq.Enumerable.Min<Banshee.Tests.TestCase>(System.Collections.Generic.IEnumerable<Banshee.Tests.TestCase>, System.Func<Banshee.Tests.TestCase,double?>)' and `System.Linq.Enumerable.Min<Banshee.Tests.TestCase>(System.Collections.Generic.IEnumerable<Banshee.Tests.TestCase>, System.Func<Banshee.Tests.TestCase,double>)'
/usr/lib/mono/gac/System.Core/3.5.0.0__b77a5c561934e089/System.Core.dll (Location of the symbol related to previous error)
/usr/lib/mono/gac/System.Core/3.5.0.0__b77a5c561934e089/System.Core.dll (Location of the symbol related to previous error)

so any ideas where to go from here?

i found this on nabble but don't know how to edit the file in question for workaround:
[http://www.nabble.com/1.5.0-Error-after-%22make%22-td24011281.html]("http://www.nabble.com/1.5.0-Error-after-%22make%22-td24011281.html")

The compiler on Intrepid has a bug, apparently

---

### Post by brookie on 2009-07-26
ok, 
the nabble post said a workaround would be to:
"In the meantime, you could work around the problem by editing
Makefile.am in tests or tests/Analyzer to disable the compilation of
Analyzer.exe. It's not needed for runnning banshee."

...so I found Makefile.am in the banshee directory I was working in /tests/Analyzer

cat Makefile.am shows:

include $(top_srcdir)/build/build.environment.mk

ANALYZER_EXE = Analyzer.exe


ALL_TARGETS = $(ANALYZER_EXE)

$(ANALYZER_EXE): Analyzer.cs
	$(MCS) -r:System.Xml.Linq -r:$(DIR_BIN)/Hyena.dll -debug+ -out:$@ $<

all: $(ALL_TARGETS)

EXTRA_DIST = Analyzer.cs

CLEANFILES = *.exe *.mdb
MAINTAINERCLEANFILES = Makefile.in

...so I just have to comment out the include or something???

---

### Post by brookie on 2009-07-26
okay that was fun but it didn't work again so i did
make uninstall (which uninstalled lots of stuff)

then, 
sudo apt-get autoclean (found nothing)

sudo deborphan | xargs sudo apt-get -y remove --purge (found lots of stuff and said to use apt-get autoremove to remove the leftover packages)

opened Synaptic Package Manager and - 
looked for Custom Filters/Orphaned packages (none)
looked in Status/Installed Residual Config (removed 3 packages)


hope that's a BIG undo
thanks for checking in and trying to help
cheers, 
brook

---

