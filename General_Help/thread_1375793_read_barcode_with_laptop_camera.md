---
title: "read barcode with laptop camera?"
date: 2010-01-08
forum: General Help
---

### Post by tlroche on 2010-01-08
Is there software that will allow one to read barcodes with one's laptop camera? Why I ask:

I am required to log attendance to a seminar. Fortunately all attendees have cards with barcodes encoding an ID number, and I am provided with a barcode scanner (Wasp WLS9500) that works as a keyboard: i.e. I connect the Wasp to a [Starling netbook]("http://system76.com/product_info.php?products_id=92") via USB, press the trigger to scan the barcode, and the ID# gets typed into the current foreground app (e.g. emacs). I can then run a script that updates the instructor's spreadsheet regarding attendance.

I'm wondering, is there software that would allow me to read the barcodes with the netbook's camera? That would mean I could just shlep the netbook (or other camera-equipped laptop) without an external barcode scanner.

---

### Post by michy99 on 2010-01-08
Theoretically, software could be written to do such a thing, but I am unaware of anyone having done so. I think you're stuck with the scanner.

---

### Post by juancarlospaco on 2010-01-08
***As you wish...***

[[IMG]http://jlinbar.sourceforge.net/JLinBar-0.03-ISBN.png[/IMG]]("http://jlinbar.sourceforge.net/")

:)

---

### Post by junapp on 2010-01-08
can you just type the barcode digits?

edit:
re-read your post. I thought you were an attendee, just trying to enter your own barcode - you seem to be the instructor in which case typing each attendee's id is not an option.

---

### Post by oldfred on 2010-01-08
If you go into synaptic for "bar codes" there are several libraries listed that convert various bar codes. I do not know how to use them though.

ZBar is a library for scanning and decoding bar codes from various sources
such as video streams, image files or raw intensity sensors. It supports EAN,
UPC, Code 128, Code 39 and Interleaved 2 of 5.

This package contains basic applications for decoding captured bar code images
and using a video4linux device (e.g. webcam) as a bar code scanner.

---

### Post by tlroche on 2010-01-11
juancarlospaco: Interesting! I'm wondering, what app did you use for that?

It looks sorta like what I want, except that the barcodes I need to scan don't also have the characters on them, so if this is just OCR, it won't Work For Me.

---

### Post by pricetech on 2010-01-11
I won't swear to it, but I think it was a tongue in cheek response.

---

### Post by StrungOut101 on 2010-09-01
usb video device
failed to connect to camera /dev/video0

---

### Post by Zorael on 2010-09-01
> **StrungOut101 said:**
> usb video device
failed to connect to camera /dev/video0

Wild guess, but I think the application uses Video4Linux 1, and your driver is Video4Linux 2. There is a wrapper library that may let you use it anyway. Try starting it with the following command;
```
**LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so** *<command>*
```

Replace *<command>* with the name of the program's binary. It wasn't obvious from your post what program you're referring to.

---

### Post by no2498 on 2010-09-01
nBar

Download JLinBar 

Project detail and discuss 

Get support 

Project Wiki 	Project Information 
About this project: 

JLinBar is a Java program that allows you to continuously scan barcodes on your computer using a webcam.
Currently it only supports Video for Linux (V4L/V4L2) webcam devices, therefore it will only work on Linux. 
 

The program's initial relase contains very little original code, being mostly glue for V4L4J and ZXing. 

The program can recognize all barcode formats supported by ZXing - including UPC-A and UPC-E, EAN-8 and EAN-13, Code 39, Code 128, QR Code and ITF. 

Planned features: 
Barcode database for automatic item recognition 
UPC Database support for database import 
A more useful GUI 
Links to relevant applications (CD / book collections managers, ERP / inventory etc.) 
A plugin mechanism to support third-party applications that leverage barcode scanning functionality 



This project was first released (version 0.03) to the public on SourceForge.net on Christmas Day 2009 
Developers 
Wanted: 

This project needs Java developers, testers and as should be obvious web developers, GUI developers / designers and graphics designers. 

Suggestions for features, bug reports, documentation and any other contributions are also very welcome. 

I only use Linux on the desktop, so I wouldn't know where to start with webcam support for other platforms. If anyone out there can give me some hints or can even bridge with another webcam subsystem, I will be more than happy to work with them to make things like auto-detection and auto-configuration work - as time allows, of course! 
Join this project: 

Please follow instructions on the project summary page. 
Get the source code: 

Source code for this project is available through the Subversion SCM repository: 
	svn co [https://https://jlinbar.svn.sourceforge.net/svnroot/jlinbar](https://https://jlinbar.svn.sourceforge.net/svnroot/jlinbar)

The repository code includes a .project file for Eclipse. Quick-start documentation is available on the Project Wiki





this is what juancarlospaco used click his pic

---

### Post by blackest_knight on 2010-09-09
its a bit fiddly you need the jlinbar.jar 
V4L4J theres a deb file for that 

but ZXing is a bit more fiddly nothing obvious to install that.

---

### Post by eode on 2012-07-15
I know this is a dead thread, but in case anyone stumbles across it.

The zbar-tools package (which includes zbarcam and zbarimg) will allow you to use your webcam (or an image) to read a barcode.


Command line:
zbarcam
or
zbarcam -nodisplay  # (to disable video window)

..this will spit out any barcodes it sees, including the barcode type.

Example output:
EAN-13:0766397444024
EAN-13:0016728123327


..now, those are a couple of CDs I just scanned, but this program has a terrible time with my very fuzzy laptop camera, and I have to hold it right and avoid bad lighting angles.  It helps to have a camera that can handle motion and that produces good, crisp images.

If you have video on, and see red dots, it recognizes there's a barcode to read, but is having difficulty reading it.  Green dots indicate a successful read.

---

