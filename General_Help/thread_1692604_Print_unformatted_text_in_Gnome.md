---
title: "Print unformatted text in Gnome"
date: 2011-02-21
forum: General Help
---

### Post by shinobitux on 2011-02-21
Hello.

I need to print raw text to a label printer I have. By filling a text file with the appropriate command codes and using the lp command I can successfully print the labels from any linux computer on the network.

My problem is...can I do the same from a GUI text editor? gedit and others seem to put headers, footers, and font declarations in the print job. Is there any way to do like Windows Notepad/tab and just print the content without the formatting?

I mean, I can print from the command line just fine...but other users wouldn't appreciate it.

---

### Post by dnairb on 2011-02-21
In gedit:

ctrl+p to open the print dialog.
In the "text editor" tab you can change various options, which should work for you.

---

### Post by shinobitux on 2011-02-21
Hello, dnairb.

Unfortunately, I have already tried that.

I go into gedit, File -> Print, Text-Editor Tab and uncheck "Print Syntax Highlighting", "Print Line Numbers", "Enable Text wrapping", "Do not split words over two lines", and "Print Page Headers".

It's still not printing.

I've read one or two forums that say the issue could be related to libgnomeprint formatting the job as postscript, but I don't know for a fact that that's the issue.

Again, Linux lp and Windows notepad work. Every GUI editor I've tried in Linux so far doesn't.

---

### Post by dnairb on 2011-02-21
I'm sorry that didn't help. I wouldn't know where to go from here.

---

### Post by shinobitux on 2011-02-21
I downloaded enscript to manually send postscript data to the printer. Using the command

```
enscript -PLabel_Printer -h testfile
```

I get the error: 

```

lpr: Unsupported format 'application/postscript'!
[ 1 pages * 1 copy ] sent to Label_Printer

```

So, it *looks* like the problem is with CUPS not taking the application/postscript mime-type...at least not correctly.

So...maybe I should rename this post to establish this as a CUPS/Postscript issue.

---

### Post by AlphaLexman on 2011-02-21
Have you pointed a web browser to:
```
http://localhost:631
```and tweaked the settings there?
I don't know if that will find your solution, but there is a lot of options to configure.

---

### Post by shinobitux on 2011-02-21
Hello, AlphaLexman.

I have looked at the CUPS web interface before...but I'll double-check all of the settings to see if there's something I missed.

...

Unfortunately, I don't see any pertinent options. The printer is set as Generic text-only and I know CUPS is working since I can print to the printer from Windows using SMB and from other Linux workstations using lp.

---

