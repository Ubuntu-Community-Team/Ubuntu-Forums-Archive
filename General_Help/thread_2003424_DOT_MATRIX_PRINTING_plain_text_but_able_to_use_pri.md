---
title: "DOT MATRIX PRINTING: plain text but able to use printer BOLD, ITALICS font"
date: 2012-06-14
forum: General Help
---

### Post by wowiesy on 2012-06-14
Hi,

Our firm has decided that transactional reports (Invoices, Shipments, etc) will be using old reliable dot matrix printers (Epson 9pin / 24pin models).  Since multi part forms are in use, and the voluminous transactions that need to be printed - a requirement then is that the reports use mono spaced fonts, at best use the native fonts of the printer being used. 

I have gathered that setting up a raw queue, and sending a plain text file to that raw queue can allow me to print the report on the multi part form this way, however, there may be occassions that some portion of the report need to be in BOLD or UNDERLINED or ITALICIZED (like say in TOTAL in the case of an invoice)...   

Since we are generating the plain text report already "formatted" in the proper columns, each placed in their respective places in the multi part forms, I figure perhaps embedding markup for the BOLD, ITALICS, UNDERLINED text would help the printer distinguish which text to print in BOLD / ITALICS / UNDERLINED depending on the markup... seems like a job for a custom CUPS filter... but I don't know where to start... 

does this make sense?

---

### Post by Zill on 2012-06-14
It is many years since I have played around with dot-matrix printers and so I may be well off the mark here but I suggest you take a look at embedding the appropriate escape codes *within* your formatted text file, rather than trying to do this subsequently via a CUPS filter.

With your example, to **bold** the word "TOTAL", add "ESC E" at the start of the word and "ESC F" at the end of the word.  You can add similar Escape Codes for the other attributes you require.  See the following links for more info:

[ESC/P (Epson Standard Code for Printers)]("http://en.wikipedia.org/wiki/ESC/P")
[Epson Escape Codes (ESC/P-83)]("http://webpages.charter.net/dperr/links/esc_p83.htm")

---

