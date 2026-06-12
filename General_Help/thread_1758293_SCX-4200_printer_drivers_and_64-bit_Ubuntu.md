---
title: "SCX-4200 printer drivers and 64-bit Ubuntu"
date: 2011-05-14
forum: General Help
---

### Post by james_mcl on 2011-05-14
Hi,

A long time ago, I bought an SCX-4200 printer, installed the 32-bit drivers from (either the CD, or Samsung's site - forget which) and all was well. *Very* well.

Several years later, 64-bit Ubuntu Natty recognised the printer the moment I first plugged it in, without my having to install additional proprietary drivers. So far, so good...

Unfortunately, when I tried to print a colour image ([http://factorfictionpress.co.uk/webcomic/comics/2008-03-22-SOTH1.jpg](http://factorfictionpress.co.uk/webcomic/comics/2008-03-22-SOTH1.jpg))
instead of its previous smooth use of different grey tones to represent the colour, the pages are now covered in "dithering" patterns as if not enough shades of grey are actually available - and the result looks a lot worse than under Hardy.

The Linux driver that used to be on Samsung's site is gone, and although I'm still looking for the CD-ROM I'm pretty sure it only had a 32-bit Linux driver. System - Administration - Printing doesn't appear to yield any helpful options either.

So, my questions are:

1.) If I setup a partiton with 32-bit Natty or Lucid on it, will there be any problems if I just install the drivers on that that worked so well with 32-bit Hardy?

2.) Does anyone have any ideas as to how I can go about addressing my print quality problems in my current 64-bit install?

Thanks,

James McLaughlin.

---

### Post by guidotrueb on 2011-05-16
You should try downloading driver from Samsung website:
[http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=br&CttFileID=2047004&CDCttType=DR&ModelType=N&ModelName=SCX-4200&VPath=DR/200902/20090225140447171/UnifiedLinuxDriver.tar.gz](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=br&CttFileID=2047004&CDCttType=DR&ModelType=N&ModelName=SCX-4200&VPath=DR/200902/20090225140447171/UnifiedLinuxDriver.tar.gz)

and run ./cdroot/autorun as root (super user) to configure it.

I hope this will help you.

---

### Post by james_mcl on 2011-05-16
The .tar.gz file looks interesting - especially the x86-64 folder - but could you tell me how on earth you found it? I can't find the file by using a Google search restricted to samsung.com, or by navigating through Samsung's site - in fact your link in the above post is the only evidence it exists at all.

Is there any page with any documentation for the Unified Linux Driver?

Oh, and thanks for the link!

---

### Post by james_mcl on 2011-05-19
I've just found (and tested) a rather neater way to deal with the Unified Linux Driver.

Another forum user (going by the pseudonym tweedledee) has set up a repository allowing the latest version of the Unified Printer Driver to be installed via Synaptic. After uninstalling splix, I went to

[http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

and followed the instructions there, installing:

samsungmfp-configurator-data
samsungmfp-configurator-qt4
samsungmfp-data
samsungmfp-driver
samsungmfp-eglibc32
samsungmfp-lpr
samsungmfp-netdiscovery-oldlibc
samsungmfp-scanner

(Actually I haven't tried to scan anything yet; I very rarely need to. But the printer quality is now much improved and back to its former smoothness.)

More information at (among others)
[http://ubuntuforums.org/archive/index.php/t-341621-p-3.html](http://ubuntuforums.org/archive/index.php/t-341621-p-3.html)
[http://www.openprinting.org/printer/Samsung/Samsung-SCX-4200](http://www.openprinting.org/printer/Samsung/Samsung-SCX-4200)

Many thanks to tweedledee if you ever read this!

---

### Post by esoniat on 2012-04-08
This worked very well.  It did not fix the problem I was having using "scanimage" but it did add a "scanner" entry to the drop down menu that also has "printers".  The "scanner" entry is a reference to "simple-scan" and it works quite well.

---

