---
title: "Epson Stylus D78 printer - &quot;/usr/lib/cups/filter/pstoraster failed&quot;"
date: 2009-07-06
forum: General Help
---

### Post by t0p on 2009-07-06
I've got an Epson Stylus D78 printer, which according to the [OpenPrinting database]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_D78") "works mostly".  I tried to get this printer working before - got new ink cartridges, made sure plenty of paper was available - but there was some kind of problem even though everything said it was okay - when I selected to print a test page, ubuntu would tell me the job was queued, but it never got done.

I got bored with it eventually and just stuck the printer away in a cupboard.  But today in a post on this forum I saw how you can do CUPS configuration through Firefox at [http://localhost:631/](http://localhost:631/).  So I've cracked out the printer again and I'm giving it another go.

When I click on the Printers tab, it shows the PDF "printer" and the D78.  But next to the name D78 it also says

> "/usr/lib/cups/filter/pstoraster failed"

Maybe it's just me, but that doesn't look right.

Despite that, it says

> Printer State: idle, accepting jobs, published. 

So I figure I can print a test page.  I select to do that, and it says it's working:

> State: processing since Mon 06 Jul 2009 20:29:47 BST 

but it's not doing anything!

When I select to do a test page with the PDF "printer", it says the job's been done.  So that seems okay.  So what's up with the Epson?  What's that stuff about "/usr/lib/cups/filter/pstoraster failed" mean?  Is there a problem with the printer itself?  I have googled that error message "/usr/lib/cups/filter/pstoraster failed", but there doesn't seem to be any consistent cause for it.  I just don't know how to diagnose this.

**EDIT:** I just rechecked printer in the CUPS config page, and it says

> "Printer busy; will retry in 5 seconds..."

*Busy*? What the heck's that mean??  I haven't told it to do anything other than print that test page - which it still hasn't done even though I've been waiting for over 15 minutes now.  *Grrr...*

---

