---
title: "Printing to PDF via command line?"
date: 2011-06-29
forum: General Help
---

### Post by mocha on 2011-06-29
I'm trying to print general documents to PDF using cups-pdf via the command line and still get the same formatted output that GUI apps provide via the printing manager in the desktop environment.

I'm fully aware of using the command line like this:

```
lpr -P Generic-CUPS-PDF-Printer filename
```

This works but it doesn't provide the same formatting that you get when using the GUI print manger/spooler.  I assume this is because many more options are passed to lpr? or is the gs program being used instead?

I attempted to capture the command that is being sent by the print spooler using ps and watch and sending it into a log file, but it's putting a lot of junk characters into my log file and I don't see the command.

---

