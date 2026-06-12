---
title: "Printing PDF files with 10.10"
date: 2010-10-26
forum: General Help
---

### Post by ocirne94 on 2010-10-26
Hi all,
I have recently upgraded to Maverick, but I no more manage to print PDF files, neither with Okular nor with Adobe Reader for Linux. The only way I have is to directly use lpr, but it's long work.
My printer is an hp deskjet 5150.
Any tips?
Thanks,
Ocirne

---

### Post by Old *ix Geek on 2010-10-26
> **ocirne94 said:**
> Hi all,
I have recently upgraded to Maverick, but I no more manage to print PDF files, neither with Okular nor with Adobe Reader for Linux. The only way I have is to directly use lpr, but it's long work.
My printer is an hp deskjet 5150.It would help if you provided more info. For example, what exactly happens when you try to print a PDF from within a reader? Are there error messages? What happens?

---

### Post by ocirne94 on 2010-10-27
Sorry for being uncomplete,
when I try to print from within a reader I get at once two notifications, one with "Started a print job" and the other with "Print job was completed"; in the jobs queue, the PDF job appears but with the flag "stopped", and there's no way to restart it.
Ocirne

---

### Post by ocirne94 on 2010-11-02
Nobody out there?

---

### Post by Zorael on 2010-11-02
If you open up the CUPS interface in a browser ([http://localhost:631](http://localhost:631)), are there any other error messages listed by the print job?

---

### Post by ocirne94 on 2010-11-02
Yes, under "status" I see
```

stopped 
"May not be a PDF file (continuing anyway)"

```
But the test file is definitely a PDF...

Trying to restart the print leads to the following:
```

stopped 
"/usr/lib/cups/filter/pstopdf failed"

```

Ocirne

---

### Post by ocirne94 on 2010-11-05
Anybody out there?

---

### Post by Zorael on 2010-11-05
I don't know enough of pstopdf to help with diagnosis from this point onwards, sorry. You could check the logs in **/var/log/cups/** to see if any more verbose errors are logged.

---

### Post by cgb on 2010-11-05
have you tried reinstalling the driver?  Also I once had a strange pdf printing issue similar to yours and for whatever reason it seemed to fix itself by duplicating the printer.  What I did was open administration/printing then right click on the printer and select duplicate. Now try printing the same document from this newly created duplicate.  If it works just delete the old and set this as default..

---

### Post by ocirne94 on 2010-11-06
No luck even after these operations;
but looking into error_log may be useful:

```

D [06/Nov/2010:12:32:24 +0100] [Job 380] prnt/hpcups/HPCupsFilter.cpp 505: cupsRasterOpen failed, fd = 0
D [06/Nov/2010:12:32:24 +0100] [Job 380] prnt/backend/hp.c 839: ERROR: null print job total=0

```

and

```

E [06/Nov/2010:12:32:24 +0100] [Job 380] May not be a PDF file (continuing anyway)
E [06/Nov/2010:12:32:24 +0100] [Job 380] PDF file is damaged - attempting to reconstruct xref table...
E [06/Nov/2010:12:32:24 +0100] [Job 380] Couldn't find trailer dictionary
E [06/Nov/2010:12:32:24 +0100] [Job 380] Couldn't read xref table
E [06/Nov/2010:12:32:24 +0100] [Job 380] Job stopped due to filter errors; please consult the error_log file for details.

```

Any ideas?
Thanks
Ocirne

---

### Post by cgb on 2010-11-08
Possibly installing ghostscript-cups through synaptic could resolve the issue per the link below.  Seems like it may be a related issue although you may already have this package installed...

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522722]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522722")

---

### Post by ocirne94 on 2010-11-09
I'm sorry but I already have that package installed.:(
Ocirne

---

### Post by cgb on 2010-11-09
Running out of ideas myself, maybe try reinstalling cups or possibly see if there is a different version of cups that can be installed.  

```
sudo apt-get install --reinstall cups
```

---

### Post by mutant_matt on 2011-10-29
I am getting these exact same errors (well, someone else that I am supporting is).  Details:

Kubuntu 10.04 LTS
3 Printers (HP C4400, DeskJet 1050, Deskjet 5500)

Native (Linux/Kubuntu) printing from any printer works fine, and from any app under Wine, printing to the C4400 works fine.  However, any printing from any Wine app, to the two Deskjets, fail in this manor (of the rest of the previous thread).  Wine is creating the postscript file fine, and using "lp <wine_generated_ps_file>", this prints fine then.  Wine thinks it has printed, and it gets stuck it seems, passing through CUPS.

I can't figure out where to look (everywhere I have looked, I can't find anything wrong).  The PPD files must be ok because native apps print fine, Wine config (not that there is really any for printing via CUPS) must be fine, as the C4400 prints.  I have also removed and re-installed the DJ1050, just in case, but still no luck.

Workaround right now, is to print to PDF file (cups-pdf installed, Wine calls this printer "PDF"), and then print the PDF file natively.  Bit of a faf, but do-able...

Anybody?

Cheers,

Matt.

---

