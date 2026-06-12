---
title: "Adding Printers and PDF editing/creation"
date: 2009-07-29
forum: General Help
---

### Post by Howard Kaikow on 2009-07-29
I  have instaled Ubuntu 9.04 on a desktop.

The desktop has an Optra-E312 connected to its parallel port.
There is also networked printer on a router, Brother HL-2170.

I had no trouble adding the Brother printer, but there is no sign of the Optra-E312.

My choices are now:

Print to File
Brother HL-2170

How do I get Ubuntu to see the Optra-E312?

Also, the E312 can automatically detect Postscript, so I should be able top send Postscript directly to the printer, as well as to a file.

What are the recommended PDF creating apps, and which allow editing of the PDF?

---

### Post by AndyCee on 2009-07-29
I realise this isn't exactly what you're asking, but openoffice is a good place for creating PDF files (and obviously saving and editing them before making them PDF's).

For the Lexmark printer, you can try installing the driver [here]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_E312"). This database has helped me many times.

If this doesn't work, try setting it up manually:

```
sudo update-pciids
```

System->Administration->Printing->New Printer->...

and see if you can connect to it there. I can see the printer in the CUPS database on my laptop, and it is a PS printer so I'm not sure why it's not auto-detecting.

<Very fussy solution>
If it's a big problem, you could try getting a LiveCD of another linux distribution (which should autodetect the printer - Mandriva or Fedora), check the printer properties properties (specifically its URI property) and put that in the appropriate field in the new printer page in Ubuntu.
</Fussy solution>

---

### Post by wojox on 2009-07-29
This may help as well:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

And in Open Office you may need this extension:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by Howard Kaikow on 2009-07-29
> **AndyCee said:**
> I realise this isn't exactly what you're asking, but openoffice is a good place for creating PDF files (and obviously saving and editing them before making them PDF's).

Most of the PDF saving I do is printing web pages, e.g., financial statments, and poorly done HTML (Microsoft!, and other sites) that will not print properly from HTML.

> **AndyCee said:**
> For the Lexmark printer, you can try installing the driver [here]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_E312"). This database has helped me many times.

I saw that last night, but I am puzzled as to what browser they expect us to use. Try printing that page, or the one for the Brother HL-2170W. The fonts are crappola, and unreadable.

> **AndyCee said:**
> If this doesn't work, try setting it up manually:

```
sudo update-pciids
```

System->Administration->Printing->New Printer->...

and see if you can connect to it there. I can see the printer in the CUPS database on my laptop, and it is a PS printer so I'm not sure why it's not auto-detecting.

As I recall, I tried that. Printer was not detected.
Indeed, the parallel port was not even listed.

There were a few other strange things listed, maybe one of them was the E312, but called by a different name?

Also, I do not know if CUPS is alreasy installed. Might have to add CUPS.

> **AndyCee said:**
> <Very fussy solution>
If it's a big problem, you could try getting a LiveCD of another linux distribution (which should autodetect the printer - Mandriva or Fedora), check the printer properties properties (specifically its URI property) and put that in the appropriate field in the new printer page in Ubuntu.
</Fussy solution>

I forget whether the Ubuntu Live CD detected the E312.

Regarding PDF creating/editing apps, I am talking about an app that would allow one to edit, say, an IRS tax form and save the ediited file as PDF. 2+ years ago, in Ubutu 7.04, I tried a particulatr app. I was shocked that I could not edit the tax forms. I won't mention that app at this time, as it has been over 2 years, maybe things have improved.

In effect, I am looking for the equivalent of NitroPDF, or CutePDF, or the full Acrobat product, or Scansoft PDF Professional, or ... .

---

### Post by Howard Kaikow on 2009-07-29
> **wojox said:**
> This may help as well:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

Thanx, I'll take a look.

> **wojox said:**
> And in Open Office you may need this extension:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

I'm looking for a general solution.
The description of the extension indicates that the critter would  not be general.

---

### Post by Howard Kaikow on 2009-07-29
> **wojox said:**
> This may help as well:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

A ha!

There is a bug in 9.04 detecting parallel ports!

> In order to get a printer detected that is connected via the parallel port you will need to load the parport_pc module as documented in [bug 369850]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/369850").

---

### Post by Howard Kaikow on 2009-07-29
> In order to get a printer detected that is connected via the parallel port you will need to load the parport_pc module as documented in [bug 369850]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/369850").

My reading of [bug 369850]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/369850") makes me believe that there is no definitive fix yet.

Guess I'll just use the other printer until there is fix in an update, so I'll have remember to check Add Printer afte each update.

---

### Post by Howard Kaikow on 2009-11-01
Has this bug been corrected in 9.10?

---

