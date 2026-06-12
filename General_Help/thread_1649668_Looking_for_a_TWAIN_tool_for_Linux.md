---
title: "Looking for a TWAIN tool for Linux"
date: 2010-12-20
forum: General Help
---

### Post by Skaperen on 2010-12-20
I am looking for a NATIVE Linux tool (e.g. does NOT require WINE) to operate a scanner using the TWAIN protocol over USB.  I found a package called "twain" but it appears to not be a package.  The following message is produced by attempting to install it:

```
E: Package 'twain' has no installation candidate
```The following information is produced about it by the "aptitude show twain" command:```
No current or candidate version found for twain
Package: twain
State: not a real package
```I'm looking for a real package, of course.

---

### Post by nerdy_kid on 2010-12-20
would xsane do the trick?

---

### Post by Skaperen on 2010-12-20
I don't know.  How well would xsane work on TWAIN devices that SANE (is it supposed to be using TWAIN?) lists on its supported devices page as not supported?

[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

I'm actually considering a Plustek 7400 slide scanner.  That's not listed at all.  The Plustek 7200 is listed as "Unsupported".  But I did not get the information that SANE uses TWAIN.  So I figured it was just working direct.  If this can't work I suppose the next question to ask would "who knows what quality slide scanner will work correctly with Linux?" over in the hardware category.

---

### Post by JKyleOKC on 2010-12-20
Xsane does work direct, but it's quite possible that it will support your scanner even though nothing shows up in its lists. I used it for a couple of years with a Umax scanner that was not listed as being supported.

TWAIN is a Windows-only package, to the best of my knowledge, that provides a wrapper (created by the scanner makers for each different scanner) with a standardized API. At one time, I was involved in attempting to create some of those wrappers for high-dollar professional units (used by banks to scan thousands of checks per day) and had the full set of TWAIN development tools. It turned out to be unable to deal with the speed required; we had to work directly with the hardware and could not go through TWAIN at all.

SANE is basically an open-source equivalent to TWAIN and has the same goal: providing a standardized API. It's a command-line package; xsane is a GUI application that uses the SANE back-end to connect to the scanner.

If you have the information on getting the scanner to work by direct commands, you might be able to get someone to create a SANE driver for it -- all needed details for the SANE API are available on the web.

---

### Post by Skaperen on 2010-12-20
> **JKyleOKC said:**
> Xsane does work direct, but it's quite possible that it will support your scanner even though nothing shows up in its lists. I used it for a couple of years with a Umax scanner that was not listed as being supported.

TWAIN is a Windows-only package, to the best of my knowledge, that provides a wrapper (created by the scanner makers for each different scanner) with a standardized API. At one time, I was involved in attempting to create some of those wrappers for high-dollar professional units (used by banks to scan thousands of checks per day) and had the full set of TWAIN development tools. It turned out to be unable to deal with the speed required; we had to work directly with the hardware and could not go through TWAIN at all.
OK, if TWAIN is just an API to a manufacturer provided driver, then I can see that being an issue.  I see lots of really bad APIs around (like ODBC) that force programs to bend over backwards and do ungodly things just to get a little bit done.  I remember a case back about 10 years ago accessing a special high speed database with an API that forced my code to end up receiving about 5 callbacks for every COLUMN of every row of a database, completely negating all the speeds supposedly gained.  I see some issues like that even with the APIs for dealing with sound cards in Linux.  Too many bad APIs around.

> **JKyleOKC said:**
> SANE is basically an open-source equivalent to TWAIN and has the same goal: providing a standardized API. It's a command-line package; xsane is a GUI application that uses the SANE back-end to connect to the scanner.But someone needs to write the part that talks to the device?

> **JKyleOKC said:**
> If you have the information on getting the scanner to work by direct commands, you might be able to get someone to create a SANE driver for it -- all needed details for the SANE API are available on the web.I have no such information at all.  If I could make it work directly, I would probably not need SANE at all.  I don't care about making it accessible from applications.  I only want to grab the pictures and store them to a file (much like I had shot them with a camera).  If the scanner had a way to behave like a camera with a CF or SD card, or a USB memory stick, I'd just do that.

If the SANE project says it is unsupported, I don't want to be buying what may well turn into a $400+ doorstop (my old Sun IPX has dibs on that job, anyway).

I have not purchased any scanner, yet.  So there's nothing to test with to see if it would work.  If the Plustek 7400 won't work, would I keep buying others until I run across something that does?  Cross checking the hardware support list against the product lists of many retailers is going to be the long hard slog.  But I guess that appears to be what I must do.

---

### Post by JKyleOKC on 2010-12-20
Since you don't yet have the scanner, my recommendation would be to go through the SANE/XSANE list of supported devices to see if anything there meets your needs.

The xsane program itself works very well, to scan and optionally do some color adjusting during the scan.

The only reason I'm not still using it is that the Umax scanner began to deteriorate and no longer gave good color reproduction, so I replaced it with an inexpensive (less than $50 on sale) Epson Stylus all-in-one -- and Epson makes available (for free) native Linux drivers for their current models. I did give up the ability to easily scan negatives and transparencies, however. But the Umax still works and does have that ability, so if I ever need it again I can get by...

---

### Post by Skaperen on 2010-12-21
> **JKyleOKC said:**
> Since you don't yet have the scanner, my recommendation would be to go through the SANE/XSANE list of supported devices to see if anything there meets your needs.

The xsane program itself works very well, to scan and optionally do some color adjusting during the scan.

The only reason I'm not still using it is that the Umax scanner began to deteriorate and no longer gave good color reproduction, so I replaced it with an inexpensive (less than $50 on sale) Epson Stylus all-in-one -- and Epson makes available (for free) native Linux drivers for their current models. I did give up the ability to easily scan negatives and transparencies, however. But the Umax still works and does have that ability, so if I ever need it again I can get by...

Maybe Epson does make a slide/negative/film scanner I could use, that has Linux drivers?

---

### Post by JKyleOKC on 2010-12-21
Take a look at the "Perfection V300 Photo Scanner" which they say is currently on sale for just under $80 USD. It clains to include negative and transparency scanning capability. I found it at [http://www.epson.com/cgi-bin/Store'jsp/Product.do?BV_UseBVCookie=yes&sku=B11B193081](http://www.epson.com/cgi-bin/Store'jsp/Product.do?BV_UseBVCookie=yes&sku=B11B193081) but I've not checked to see if they provide Linux drivers for it...

EDIT: When I checked the link it told me it had expired, but gave me a page that let me get back to their offerings by first selecting "Scanners" and then selecting the "Photo" group...

Second EDIT: Apparently they do provide a native Linux driver for it, although it's through a third party rather than direct from Epson. I got my drivers through that same route, and they are free of cost and work very well -- MUCH better than xsane or TWAIN, in fact, since they take advantage of all the features of the hardware rather than being generic! Just click on "drivers and support" at the top of the page and follow the links provided, and you can download the software to check out its features.

BTW, I'm not an Epson employee -- just a very satisfied user of one of their products.

---

