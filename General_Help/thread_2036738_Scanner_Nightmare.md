---
title: "Scanner Nightmare"
date: 2012-08-02
forum: General Help
---

### Post by m3grant on 2012-08-02
Hi, I'm new to Ubuntu (linux in general really) and am having a real problem installing my Epson Stylus SX525WD (one of those all in one things).

When I had finished installing Ubuntu 12.04 LTS the printer worked first time. However I've just tried to use the scanner and none of the software recognises it.

I've done a bit of searching and managed to download the Linux Scanner drivers from the Epson site, however when I try to install them the software centre gives me this error message "Dependency is not satisfiable:iscan-data" I thought I'd cracked it until that happened.

If anyone can help me get this working I will be forever in debt to you. I really dont want to have to go back to Windows but am thinking I might end up having to do so :(

Many thanks
Grant

---

### Post by Dylan1473 on 2012-08-02
What program are you using for the scanner? I've used XSane before successfully but I had to download an additional package with drivers for my particular device.

---

### Post by m3grant on 2012-08-02
Trying to use Xsane too. Just getting the "Device not found" message on startup :(

---

### Post by Dylan1473 on 2012-08-02
In all honesty I don't think this will actually help, but if you haven't already you could try installing some extra Epson printer related packages. Using sudo apt-cache search Epson I've found the following:

```

epson-escpr - transitional dummy package for epson-escpr printer driver
escputil - maintenance utility for Epson Stylus printers
gle-graphics - Interactive Graphics Language Editor
libescpr-dev - printer driver for Epson Inkjet - library development files
libescpr1 - printer driver for Epson Inkjet - shared library
libimage-exiftool-perl - Library and program to read and write meta information in multimedia files
libinklevel-dev - development files for libinklevel5
libinklevel5 - library for checking the ink level of your local printer
mtink - Status monitor tool for Epson inkjet printers
mtink-doc - Documentation for mtink
photopc - Interface to digital still cameras
printer-driver-escpr - printer driver for Epson Inkjet that use ESC/P-R

```

Just try sudo apt-get install [package name] with any of those that look like they might possibly be helpful and hope for the best. Then when that doesn't work wait for someone who knows way better than me to happen along. Sorry, I know that's not much of an answer - thought maybe I could help since I've previously had problems with an all-in-one scanner printer thingy but I think your problem might be a bit different than mine was. Where did you get the drivers from exactly?

---

