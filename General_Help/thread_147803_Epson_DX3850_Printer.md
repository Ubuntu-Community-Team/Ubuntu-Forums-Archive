---
title: "Epson DX3850 Printer"
date: 2006-03-20
forum: General Help
---

### Post by Steve- on 2006-03-20
Ok, i'm trying to install my printer in Linux. 

LinuxPrinting has recently got a page for my printer, it is supported by gutenprint
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX3850](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX3850)

After many paths, many readmes, many sets of bad documentation, many blog and forum posts and a bunch of problems I made for myself, I have managed to install gutenprint. I think.
I restarted cups but when I go to System -> Administration -> Printing and add a printer, whilst the Printer gets detected (as a DX3800, which is close enough), options on the following pages don't include the right printer.

I'm so completely lost. My brain hurts. Am I on the right path? Am I looking for something that isn't there?

Thanks, Steve.
I fully plan to write a (simple) webpage on how this is done, once I get it working, to save other people's pain.

---

### Post by cilynx on 2006-03-20
Generally, you can load the driver for the correct series of printer without having to have the model exactly.  I have an HP Photosmart 2575 that is detected as a 2575, but the driver is for the 2570.  It works perfectly.

---

### Post by Red Ghost on 2006-03-20
In Dapper gutenprint is installed by default. I just checked and there is an option for a DX3850. Consider upgrading, it's quite stable now. I have a CX4800 which works flawlessly. Just install Dapper, go to System->Administration->Printing and add a new printer. It should auto detect it and on the next page it should automatically select "Stylus DX3850 - CUPS+Gutenprint v5.0.0-rc2". Just hit apply.
[IMG]http://img113.imageshack.us/img113/5476/addprinter8rf.png[/IMG]

---

### Post by Steve- on 2006-03-21
Quite stable? Hmm. Given my ability to use Linux, I'd rather not take the risk.

I just opened the Printing panel now and found I have a printer in there.. but printing a test page has no effect. If I try and add the DX3800, when it moves forward to the next page where you choose the printer version, it defaults to a Stylus-800. I tried installing it like that and printing a test page and nothing has popped out yet.

How can I test gutenprint is happily installed?

Thanks

---

### Post by Red Ghost on 2006-03-21
Are you sure it wasn't installed to begin with? I thought it also came default on Breezy?

---

### Post by Steve- on 2006-03-22
It wasn't as far as I could tell. I could only find the help files for gimp-print, the old version of gutenprint.
I reinstalled my downloaded version, as I forgot to put 'sudo' before 'make install' last time, and now it works dandily!
Although, the test page just wasted all my ink.. hopefully I can turn that kind of stuff down.

---

### Post by kristalsoldier on 2007-02-23
> **Red Ghost said:**
> In Dapper gutenprint is installed by default. I just checked and there is an option for a DX3850. Consider upgrading, it's quite stable now. I have a CX4800 which works flawlessly. Just install Dapper, go to System->Administration->Printing and add a new printer. It should auto detect it and on the next page it should automatically select "Stylus DX3850 - CUPS+Gutenprint v5.0.0-rc2". Just hit apply.


Hi...

I get the Stylus DX3850 part, but the CUPS+Gutenprint etc...is missing.

I am however still running this off the LiveCD. Does this have anything to do with it?

At the end of it all, I end up with no printer added.

What am I missing out/ doing wrong?

Thanks.

---

