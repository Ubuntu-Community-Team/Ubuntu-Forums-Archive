---
title: "Email to Print"
date: 2012-03-05
forum: General Help
---

### Post by kronikabis on 2012-03-05
I know most people probably want the opposite.... print to an email.

What I am looking for is the opposite. It has been decided that trees are cheap and I've been asked to investigate a solution to retrieve an email, and print it directly to a printer.

Are there any applications to do this?
Scripting?

Printing a document directly to printer is easy enough.

Grabbing emails in html and preparing them to print is another story... any ideas?

Cheers,

---

### Post by sybille on 2012-03-05
Here's one idea:
[B]
Email to printer gateway[/B] [PDF]
[http://www.jasonellison.net/files/Email_to_printer_gateway.pdf](http://www.jasonellison.net/files/Email_to_printer_gateway.pdf)

---

### Post by Khayyam on 2012-03-05
> **kronikabis said:**
> [..] I've been asked to investigate a solution to retrieve an email, and print it directly to a printer.

What is an email ... are we talking text, MIME, html?
Are you looking to beautify, or do you want to simply print raw text?
Do you want to strip out headers, or should they be printed 'emails'?
Do you want to convert to some format (pdf)?

It really depends on what you need to do. I use to have a script to format emails and prepare them for the printer, but it dealt with the text only and was mostly used for printing out reports. Other than removing line returns and headers and converting to pdf is wasn't particularly fancy.

> **kronikabis said:**
> Grabbing emails in html and preparing them to print is another story... any ideas?

If the emails are html, then perhaps converting to xml would be a good start, [htmltidy](http://tidy.sourceforge.net/) will do this. You could then transform the xml to various formats using any number of tools out there, [xml2pdf](http://www.pi-sysprog.de/prod/x2p/x2pstrte.html) is one such tool.

You might also want to look at [mail2pdf](http://mail2pdf.sourceforge.net/). Most pre-preprocessing can be done via scripting, but it mostly depends on what output your looking to achieve and the nature of the input.

Hope that is of some help ...

best .. khay

---

