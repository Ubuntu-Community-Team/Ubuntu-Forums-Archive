---
title: "verbatim print to pdf from firefox"
date: 2010-12-24
forum: General Help
---

### Post by scu-ba-de-buntu on 2010-12-24
Just as in the title. Would like a pdf that looks exactly like the website. Graphics, CSS and all. 'Print to file' printer available does not do this.

(Ubuntu:10.04,firefox:3.6.13)

thanks

---

### Post by mywai on 2010-12-25
In menu bar, Applications/Accessories/Take Screenshot of the Window

Save the screenshot, open it with Image Viewer, print to file choosing pdf as output format.

---

### Post by noah++ on 2010-12-25
Go to Print -> Options and check Print Background Colors and Print Background Images. Do you get the results you want?

---

### Post by efflandt on 2010-12-25
cups-pdf package is usually good for creating pdf files.  You print to it as a printer.

However if there are scrollable areas (like code sections with enough text to vertically and/or horizontally scroll) you will not necessarily see everything within scrollable boxes.

And as noah++ mentioned, you may need to enable other things to print that might not normally be printed to save ink or toner.

---

### Post by scu-ba-de-buntu on 2010-12-26
Why can't I just print to PDF/PS a flash site or similar? It had to be assembled in memory once.

---

### Post by lisati on 2010-12-26
My first choice would be to use the "print to file" option that has already been mentioned. My next choice would be to use FireFox's File->Save As option, but that tends to save as html rather than PDF.

---

### Post by spmmoi on 2010-12-31
> **lisati said:**
> My first choice would be to use the "print to file" option that has already been mentioned. My next choice would be to use FireFox's File->Save As option, but that tends to save as html rather than PDF.
Okay, I am posting under this thread because I need help with web-page pdf printing from FireFox also. I want to be able to select portions of text on the document to print as pdf for later viewing on my machine. I have the CUPS-PDF thing setup, however the output file size is usually larger. I wish to be able to reduce the output file size. 

When I used NitroPDF freeware on Windows, text from the web site is usually under 1MB, but now, same materials would come out in 2MB or more. 

I stumbled upon this [http://milan.kupcevic.net/ghostscript-ps-pdf/](http://milan.kupcevic.net/ghostscript-ps-pdf/) While I think it may help, I do not know how to incorporate this into my "cupsd.conf" file or to overwrite my existing config and not screw things over.

Anyone have any ideas?

Thanks!

---

### Post by scu-ba-de-buntu on 2011-06-29
Solved by use of the ScreenGrab! plug-in

---

