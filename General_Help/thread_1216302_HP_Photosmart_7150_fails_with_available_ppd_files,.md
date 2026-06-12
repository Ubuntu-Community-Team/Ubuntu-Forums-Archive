---
title: "HP Photosmart 7150 fails with available ppd files, older working ppd attached"
date: 2009-07-18
forum: General Help
---

### Post by BadSquishy on 2009-07-18
I have a freshly installed Ubuntu 9.04 Server, to get my Photosmart 7150 working I installed the packages cupsys, hplip, hpijs-ppds, and foomatic-db-hpijs.  The cups and hplip packages alone got cups working and I was able to add the printer and configure the printer using the cups web interface.  I added the hpijs-ppds and foomatic-db-hpijs packages later in an attempt to find more ppd files to tryout.  With these packages installed there were three ppd files for an HP PhotoSmart 7150 to choose from when adding the printer in the Cups web interface.  Everything appeared to be working until I attempted to print.  

Printing the test page from the Cups web interface would print part of a line of text along the top edge of one page, spit out that page, print the next part of line along the top edge of the second page, spit out the page, print the next 1 line piece of the test page on the third page, spit it out, etc., etc.  

I saw the same behaviour whether I chose any one of the ppds in the list available.  I also tried downloading the ppd available for download from openprinting.org and configuring the printer with this ppd file, to no avail.  

This printer has been working well on a Gentoo box, I got it working by installing just the hpijs package back in 2005.  As a last idea I copied the ppd file stored in /etc/cups/ppd from that Gentoo box to my desktop.  I deleted then re-added the printer with the Cups web interface and browsed to the ppd file copied from the Gentoo box in the "Or Provide a PPD File:" text box.  Lo and behold, this worked!  It printed the test page very well, and with the correct server and client configurations in cupsd.conf and client.conf respectively I am able to print to this device from other linux boxes on my network.  

I have attached the working ppd file to this post, I've append .txt to the filename so it will allow the upload.  To use the attached file save it somewhere handy.  Rename the file to just "HP-PhotoSmart_7150-hpijs.ppd" without the quotes.  Using the Cups web interface (accessible by browsing to *server-ip-address:631* with our favorite web browswer) add the printer, or modify the existing, broken, photosmart 7150.  When you get to the screen where you can choose the ppd file from a list, instead click on the *Browse* button next to the "Or Provide a PPD File:" text box and choose the ppd file you've downloaded.  Hit the equivalent of OK a few times and there you go.  

Hope this helps.

- BadSquishy

---

### Post by The Cog on 2009-07-18
Good work. 

Perhaps you should report the bug on Launchpad. I submitted a PPD fix once, and in the fullness of time it made it into the release. I don't have to fix up my printer after installing any more.

---

