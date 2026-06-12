---
title: "trouble opening pdf files in firefox"
date: 2011-04-14
forum: General Help
---

### Post by r.stiltskin on 2011-04-14
Ever since I upgraded from Ubuntu 8.04 to 10.04, and thereby lost mozilla-acroread, I've been having a lot of trouble opening pdfs in a browser window.  If they open at all, there is generally a long delay before opening.  Frequently, I have to reload the page several times to get the file to open, and frequently I can't get it to open at all, and have to download the file and open it outside the browser.

For what it's worth, this is the current content of the relevant (I believe) parts of my mozpluggerrc file; I've tried playing around with it various ways but frankly it seems to make no difference -- the behavior seems the same even if I comment out EVINCE() and ACROREAD() altogether, so I really don't understand what's going on.  Is everyone having this trouble, or have you all figured out a solution?

```

### Acrobat Reader
define(ACROREAD, [repeat swallow(acroread) fill needs_xembed : acroread -openInNewWindow /a "$fragment" "$file"])

### GV
define(GV_OPTS,[--safer --quiet --antialias -geometry +9000+9000])
define(GV_FLAGS,[repeat swallow(gv) fill needs_xembed])
define(GV,[GV_FLAGS(): gv GV_OPTS() "$file"])

### Evince
define(EVINCE, [repeat swallow(evince) fill needs_xembed: evince "$file"])

## ...

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	EVINCE()
	ACROREAD()
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	repeat noisy swallow(okular) fill: okular "$file"
	GV()

```

My acroread version is 8.1.6 downloaded directly from Adobe.

---

### Post by steve161 on 2011-04-15
You should be able to install acroread in 10.04 by opening the synaptic package manager, settings-repositories-other software, check the partner repository,reload,and search for acroread.

---

### Post by r.stiltskin on 2011-04-15
I already have acroread and I have no reason to believe there is anything wrong with it -- it works fine outside of firefox, and used to work fine inside firefox with the mozilla-acroread plugin.  I assume the problem is with mozplugger, or the way I have it configured.

---

### Post by scofflan on 2011-04-20
Are you running the 64 Bit version of Ubuntu? It looks like there is a problem with acroread in when used with the 64 bit version. 

A possible workaround is to set evince as your default pdf viewer in Firefox, although I have not been able to get this to work in all instances.

---

### Post by bertilow on 2011-04-21
I get the same problem in a 32-bit version of Natty.

If mozplugger is installed, Firefox 4 offers Mozplugger as an alternative for viewing PDFs. But the actual result is that it uses Acroread - no matter what's in the configuration files for Mozplugger!

Since Acroread doesn't work very well (sometimes the PDFs are displayed, sometimes not), I'd like to use Evince instead. I can get Evince to open the PDFs outside of Firefox, but I can't make Firefox 4 embed Evince. That worked well in Firefox 3, and also with Firefox 4 in Maverick.

I suspect that, although the chosen setting for PDFs is Mozplugger, Firefox actually uses Acroread directly instead, bypassing Mozplugger. It does this even if Evince is set as the default program for PDF files in Ubuntu. Or else the actual Mozplugger settings being used are hardcoded somewhere in Firefox itself.

---

### Post by scholzilla on 2011-04-22
I'm having the same problem using Firefox 3.6.16 on 32-bit lucid, acroread current and installed. Sometimes pdfs open, more often they don't. Same deal with Chromium.

@ bertilow: have you actually uninstalled acroread and then tried mozplugger?

---

### Post by r.stiltskin on 2011-04-22
I uninstalled my acroread 8 and installed acroread 9 from medibuntu.  I also edited the pdf section of mozpluggerrc to this:
```

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
#	ACROREAD()
	repeat noisy swallow(evince) fill: evince "$file"
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	repeat noisy swallow(okular) fill: okular "$file"
	GV()
	repeat noisy fill exits: evince "$file"

```
Notice that I have commented-out the ACROREAD() macro, so I would expect that acroread would not be used by firefox at all.  Still, sometimes pdfs are opened in the browser window using evince, sometimes they open in the browser window using acroread, and sometimes they open outside the browser with evince.  I don't understand what governs which method is applied.

I can say that now the files do open one way or the other "more often than not", although sometimes I have to reload the page once or twice before they actually open, and it frequently seems to take longer than it used to before I "upgraded" to Lucid (10.04).

---

### Post by tommpogg on 2011-06-28
> **scofflan said:**
> Are you running the 64 Bit version of Ubuntu? It looks like there is a problem with acroread in when used with the 64 bit version.

I agree that acroread causes problems on 64 Bit versions of Ubuntu.
I have installed acroread and, as a consequence, I am no longer able to open pdf files from firefox; I cannot even download any pdf at all! 

As a solution, I have unistalled acroreader. Now, I cannot open pdf files in firefox, but at least I can download them and view them with evince.

PS: I am using Ubuntu 10.10

---

### Post by haqking on 2011-06-28
> **tommpogg said:**
> I agree that acroread causes problems on 64 Bit versions of Ubuntu.
I have installed acroread and, as a consequence, I am no longer able to open pdf files from firefox; I cannot even download any pdf at all! 

As a solution, I have unistalled acroreader. Now, I cannot open pdf files in firefox, but at least I can download them and view them with evince.

PS: I am using Ubuntu 10.10


I am using 10.10 and firefox and 64 bit and acroread works fine across the board with everything.

I have other PDF apps installed also, but only use adobe for viewing and PDF editor for editing.

---

### Post by spinoza666 on 2011-09-20
Hi,

I had the same problem. I sorted it by going to Firefox>Edit>Preferences>Applications, and changing 'PDF Document' from 'Use Adobe Reader 9.4 (in Firefox)' to 'Use Document Viewer (Default)'. The default is Evince in my case. Please note that this option does not embed in Firefox.

---

