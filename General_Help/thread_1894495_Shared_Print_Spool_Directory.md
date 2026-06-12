---
title: "Shared Print Spool Directory"
date: 2011-12-12
forum: General Help
---

### Post by KnevetS on 2011-12-12
My wife has a windows vista computer, and it's the only one in the house that I can't get the network printer working on.

A friend of mine long ago had his network printer set up such that he had a print-drop directory on a shared drive on his print server.

Any file dropped into that directory would be sent to the printer.

I'd like to set something like that up in ubuntu.  Even if it was simply dropping postscript files into the directory rather than, it would work better than our current process of her e-mailing me whatever she wants printed.

Unfortunately, my google-fu is a bit weak today.  My search results are turning up all kinds of information, but none related to what I actually desire.

---

### Post by KnevetS on 2011-12-14
I'm making a bit of progress.

I found **inoticoming** which will perform an action when files hit a directory.

I also found **lpr** which I can use to print from within a script, and the *lpr -r* switch that will remove a file after printed.

Apparently, lpr will print pdf files and text files just fine, but other documents are problematic.  Office files can be printed with 
**soffice** with *soffice -invisible -p /path/to/doc* - but I'm unsure if that's both *.doc and *.docx formats, and how extensive the support is for spreadsheets, presentations, and fancy formatting.  I'll have to do a little bit of testing, and soffice won't auto-delete files once the print job has been completed.

Given all of this, I think i can throw together a shell script that *inoticoming* can call.  It's not perfect, but it's something.

---

