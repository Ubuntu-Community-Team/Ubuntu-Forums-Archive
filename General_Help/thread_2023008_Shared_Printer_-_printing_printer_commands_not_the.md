---
title: "Shared Printer - printing printer commands not the Test Page"
date: 2012-07-11
forum: General Help
---

### Post by held7over on 2012-07-11
I followed the Ubuntu community directions for setting up Network Printing With Ubunut.

My Ubuntu 12.04 computer is my client computer and my Linux Mint Debian Edition 12.04 is my hosting server computer for the printer.

The LMDE system has no problem printing a test page on the printer.

However, my client computer has a strange result when I request a test page be printed from the menu brought up by the printer properties icon. Below is what that page looks like!

#PDF-BANNER
Template default-testpage.pdf
Show printer-name printer-info printer-location printer-make-and-model printer-driver-name printer-driver-version paper-size imageable-area job-id options time-at-processing

As you can see, that isn't exactly what one would expect for a test page printout! Any ideas as to what is wrong and how to fix it?

Also, I tried launching LibreOffice and created a single line "Hi There!" and selected print, but my Shared Network Printer was not in the printer selection area. Am I misunderstanding how to send documents to the printer?

Thanks for your suggestions and thoughts! :p

---

### Post by lallenlowe on 2012-07-31
bump. I am having the exact same issue. Ubuntu 12.04 client, Ubuntu 10.04 cups server, print test page from client just prints printer commands starting with #PDF_BANNER. Any help?

---

### Post by held7over on 2012-07-31
lallenlowe--  The only thing I can add, is, my shared printer now shows up in my select a printer routine.....but....I get the same results when I try to print. Also, I have no idea what changed to make it show up in the select a printer menu! It wasn't anything I did. It just suddenly started showing up when using various apps which allow printing.  Ha Ha Ha

---

### Post by DavidBooth on 2013-01-30
I have the exact same problem on Ubuntu 12.04 client, attempting to use a networked printer on an Ubuntu 10.04 server.  The printer works fine from an Ubuntu 10.04 client, so I know the problem is not with the printer or server.

Suggestions, anyone?

---

