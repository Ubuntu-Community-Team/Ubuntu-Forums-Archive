---
title: "Gnome, Qcad, Print, Printer"
date: 2006-06-27
forum: General Help
---

### Post by xerman on 2006-06-27
Hello there,

I'm using 5.10ppc on an iMac G3, the Ubuntu Flavor with Gnome, but need to use QCad, which is a QT/KDE app.

I've found the following Issues I cannot solve after diggin the internet, Qcad doc and Cups doc:

1- I cannot print directly from Qcad to the printer (HP color inkjet printer cp1700d). The printer does not appear on the Qcad printing dialog.

2- Printing to a PS file produces the right output, a .ps file that I can see with Evince, but I cannot print well:
- I have a drawing of size A3, QCad saves an output.ps file where sizeof Drawing is A3.
- When I open output.ps in Evince and choose to print to a printer, I select paper size as A3.
- The result comes out as half the drawing being printed, just an A4 fraction of the A3 Drawing.

3- Converting to PDF through ps2pdfwr produces a PDF file that is an A4 window of the A3 drawing. The only way to get an A3 PDF is by means of
```
gs -sPAPERSIZE=a3 ... output.pdf
```
- printing this pdf file through evince produces de file to print scaled to A4 in half the A3 paper.

Right now I'm pretty stuck at this point. I'll appreciate any help. By the way, te printer is an A3 printer, I checked that before buying it. ;) 

Thanks for any help.

---

### Post by TVu on 2006-07-22
>1...The printer does not appear on the Qcad printing dialog.

I have similar problem. I installed cups-pdf and set up a pdf-printer with it, but new printer does not show in qcad printing dialog. Other applications show it and use it just fine. It would be great if someone could point what file to modify to make printing dialog to show new printer.

Edit: Oh well, rebooting solved this one. Printer shows as expected.

---

### Post by Chuck_W on 2006-08-13
This seems to be a common problem. In Terminal type:

sudo ln -s /var/run/cups/printcap /etc/printcap

This creates a link that makes it possible to print from a KDE app while in Gnome. You may have to adjust paper size and other settings (in preview, I think).

hth

---

