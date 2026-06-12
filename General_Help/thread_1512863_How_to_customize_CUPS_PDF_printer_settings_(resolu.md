---
title: "How to customize CUPS PDF printer settings (resolution, grayscale, fonts etc)?"
date: 2010-06-18
forum: General Help
---

### Post by quadra on 2010-06-18
Hi there

Ubuntu 10.04

Since I could not configure the "Print to file" options, I installed cups-pdf and I try to modify its settings.
As an example, I want to print color documents to monochrome PDF files.
I know it's possible, as CUPS-PDF has many options but they're hard to configure.

I tried to modify the file /etc/cups/cups-pdf.conf

as explained in
[http://ubuntuforums.org/showthread.php?t=1479466]("http://ubuntuforums.org/showthread.php?t=1479466")


Extract of my cups-pdf.conf:

[INDENT]##############################################
#			
# PDF Conversion Settings
#
#####################################################


## Some commented-out lines here
## The GSCall line is modified and commented out:

GSCall %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -dCompressFonts=true -sOutputFile="%s" - dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -sColorConversionStrategy=Gray -dProcessColorModel=/DeviceGray -dPDFSETTINGS=/screen -c .setpdfwrite -f %s[/INDENT]


But nothing changed - printed documents are still exactly the same as with the default cups-pdf installation, not monochrome. What am I doing wrong?

---

### Post by 11hjpphty76lkjj on 2010-06-18
I could be wrong. But if I remember correctly you might want to use ghostscript to do this.

[http://pages.cs.wisc.edu/~ghost/doc/cvs/Use.htm]("http://pages.cs.wisc.edu/~ghost/doc/cvs/Use.htm")

A

---

### Post by quadra on 2010-06-20
Dear kalosaurusrex

I think you're right, but CUPS-PDF already uses Ghostscript. I think the mentioned section in cups-pdf.conf contains the parameters for the Ghostscript (gs) call, however when I modify them, there's no effect.

Can anybody help to configure the CUPS-PDF settings?
Any other suggestions about how to set default parameters for printing to PDF?
Any help very much appreciated.

---

### Post by 11hjpphty76lkjj on 2010-06-20
How about if we set cups to debug mode, then check the cups error log to see what gs string is being passed through?

You can edit the cups conf (/etc/cups/cupsd.conf) change the debug level from none to debug, restart cups, (/etc/init.d/cups restart), then look at the log; sudo tail -f /var/log/cups/error_log, finally try and print and look for the gs string and post that here. Or you can post the entire cups log using pastebin, etc.

I dunno why I didn't think of that before!

A

---

### Post by quadra on 2010-06-20
Thanks kalosaurusrex
Did what you said. In the cups log, the arguments are not the same as those I tried to set in /etc/cups/cups-pdf.conf. So we get closer: It seems that either I modify settings at the wrong place, or someone is nastily overriding them:p!

/etc/cups/cups-pdf.conf (extract):
```

GSCall %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -dCompressFonts=true -sOutputFile="%s" - dAutoRotatePages=/PageByPage -dAutoFilterColorImages=true -dColorImageFilter=/FlateEncode -sColorConversionStrategy=Gray -dProcessColorModel=/DeviceGray -dPDFSETTINGS=/screen -c .setpdfwrite -f %s
```

/var/log/cups/error_log:
```
D [20/Jun/2010:20:16:38 +0200] [Job 112] PostScript to be injected: 
D [20/Jun/2010:20:16:38 +0200] [Job 112] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
```
 
Attached is the full log for this print job

---

### Post by magicfab on 2010-06-30
The default for cups-pdf is to use gs as indicated in the config file comments.

You need to change that to ps2pdf. Search for:
#GhostScript /usr/bin/gs

and change it to:
#GhostScript /usr/bin/pstopdf

In a quick test I couldn't make this work, not even with the options suggested for Mac as mentioned in the comments.

Filing a bug would probably the best next thing.

---

### Post by landis on 2010-09-07
Were you ever able to get this working properly?

I configured a backwards way of doing it, but I was really hoping someone got it working properly.

What I did was add a new Ghost Script line to my post processing script that looks like this:
```

#!/bin/bash

FILENAME=`basename $1`
DIRNAME=`dirname $1`
DATE=`date +"%Y%m%d_%H%M%S"`

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=$1"mod" $1
rm $1
mv $1"mod" $DIRNAME"/"$DATE".pdf"

```It works yes, but it's dumb, because basically I'm printing the file twice.

---

### Post by landis on 2010-09-08
After wasting a day and a half on this I finally stumbled upon a solution.

In this launchpad discussion ([https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/600764](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/600764)) Till Kamppeter said:
> 
In Ubuntu we have a PDF-based printing workflow. All jobs arriving at  CUPS are turned to PDF by filters which ship with the CUPS package. Then  the pdftopdf CUPS filter does page management (N-up, reverse order,  selected pages, ...) and then PDF data is passed on to the driver or the  backend. As the cups-pdf backend already receives PDF this way it does  not call Ghostscript any more but simply passes the incoming PDF through  into the output file.
Basically this means the GSCall feature of CUPS-PDF doesn't work and it doesn't really sound like Ubuntu is going to change the way it works.

As a work around I followed this site that suggests using ps2pdf directly ([http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/673315301751997aca256f6c001a2941?OpenDocument](http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/673315301751997aca256f6c001a2941?OpenDocument))

---

### Post by nikamech on 2010-09-10
I have a question regarding page size.  
I need to output architectural / engineering documents for use in the US.  How do I verify the page format for the Arch page sizes,  Arch D (24"x36") and Arch E (36"x48")? 
How do I create a custom paper size for Arch E1 (30"x42")?
I've checked output with A0 size and it scales just as expected, so I believe I'm just getting the page sizes that are native to the CUPS / CUPS-PDF setup, but are not in line with established standards.

---

### Post by thewhiteeye on 2010-12-14
I have a query,
   When the cups pdf printer converts a file into a pdf file, it prints the file name on the beginning of every page. How do I change the settings so that it does not print the filename. 

e.g when i printed a text file, the following is printed at the beginning
"File: /home/srikanth/Return of Sherlock Holmes"
   Please help me...

---

