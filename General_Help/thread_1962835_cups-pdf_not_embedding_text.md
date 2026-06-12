---
title: "cups-pdf not embedding text"
date: 2012-04-21
forum: General Help
---

### Post by JohnnyVW on 2012-04-21
Hi Folks!

A few weeks ago, I finally upgraded from 10.10 to 11.10.  Not a pretty upgrade...  

Anyway... I installed the cups-pdf printer and now the pdf's come out as all images.  This happened back in 2009 and there was a patch to poppler's pdftops ([https://bugs.launchpad.net/ubuntu/+source/cups/+bug/381788](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/381788)). 

For giggles, I tried it on my current system, but it didn't work.  I tried to purge/re-install cups-pdf...  no love.

Is anyone else having this issue?  

I just tried on the laptop (11.04) and the same thing happens.

I just attached a sample.  If I print to file from Firefox, the pdf is fine.

Hmmm, the pdf is too large to attach.  Another problem...

---

### Post by JohnnyVW on 2012-04-28
Anyone?

---

### Post by peter_altherr on 2012-05-03
same here with ubuntu 12.04. this bug is so annoying as it has already been fixed in the past. i have not found any solution or workaround for this.


greetings

peter

---

### Post by JohnnyVW on 2012-05-03
Hi Peter!

Yeah, that is what has me so annoyed.  I've tried a few things, but no luck.  When the cups-pdf printer works right, it's great!  ...And convenient.

---

### Post by pt123 on 2012-05-24
I recently upgraded from 10.10 to 12.04 when cups-pdf was perfect now it's bloody useless because of this. All the text printed to PDF is bloody useless as it can't be copied it is like having paper. 

The bug is reported here
[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820)

As usual nothing has been done about it.
The usual problem problem with open source projects, features are killed off without considering common use case scenarios. 

There has to be a way of installing old working packages.

---

### Post by oliverjames on 2012-06-25
At least you're getting some output. I cannot print to pdf from anything other than LibreOffice, which suggests that the solution is not hard. Think of the paper saving, the carbon footprint etc!

This Xubuntu works pretty well but this and the inability to suspend/hibernate securely are soon going to require that I point another OS tool at my valuable data partition. 

Oliverjames

---

### Post by Cheesemill on 2012-06-25
I've never had any reason to install cups-pdf, instead I just use the 'Print to file..' option that is built into Ubuntu. Just select .pdf as the output type and it will produce a PDF file with selectable text.

---

### Post by oliverjames on 2012-06-25
Thanks Cheesemill, you're a Star. 

You wouldn't happen to know how to fix the flaky suspend / hibernate functions would you ; - )

Best regards,

Oliverjames

---

### Post by pt123 on 2012-06-28
> **Cheesemill said:**
> I've never had any reason to install cups-pdf, instead I just use the 'Print to file..' option that is built into Ubuntu. Just select .pdf as the output type and it will produce a PDF file with selectable text.

Print to file previously wasn't configurable, in Firefox it was defaulted to PostScript and you had to manually change it. Cups Printer is smarter in creating filenames, it uses the web page title to create the filename. Also the cups-pdf lets you control the DPI settings for the images in the PDF. Finally cups-pdf can be used as a network printer.

---

### Post by JohnnyVW on 2012-08-05
> **pt123 said:**
> Print to file previously wasn't configurable, in Firefox it was defaulted to PostScript and you had to manually change it. Cups Printer is smarter in creating filenames, it uses the web page title to create the filename. Also the cups-pdf lets you control the DPI settings for the images in the PDF. Finally cups-pdf can be used as a network printer.

Agreed.  Yes, for now I'm using the print to file option, but it's not a solution.  

It seems to be working in other distros...  Can't wrap my head around why it doesn't work in Ubuntu.  

I recently upgraded to 12.04.  Same problem.  :(

---

### Post by pt123 on 2012-08-05
> **JohnnyVW said:**
> Agreed.  Yes, for now I'm using the print to file option, but it's not a solution.  

It seems to be working in other distros...  Can't wrap my head around why it doesn't work in Ubuntu.  

I recently upgraded to 12.04.  Same problem.  :(

Which distros and do you know what version of cups they were using?

---

### Post by leorolla on 2012-08-21
When someone finds a workaround or a good distribution, please post here.

---

### Post by oliverjames on 2012-08-21
> **leorolla said:**
> When someone finds a workaround or a good distribution, please post here.

After recent CUPS updates it's now working for me in Xubuntu. My only issue with this option now is that the PDF copy is automatically given the parent file name and saved in the PDF folder in my home directory. Ideally I prefer to choose the save location and file name.

Still this Xubuntu installation is so good in all other respects that I cannot really complain.:p

---

### Post by pt123 on 2012-08-21
> **oliverjames said:**
> After recent CUPS updates it's now working for me in Xubuntu.
Can you provide us with the version you are running and are you using Xubuntu 12.04?

I tried it after the recent update, some of word in the text is selectable on page 2. But when you paste it's all gibberish. 
[ATTACH]222993[/ATTACH]
> 
 My only issue with this option now is that the PDF copy is automatically given the parent file name and saved in the PDF folder in my home directory. Ideally I prefer to choose the save location and file name.
It's alway been like that.

---

### Post by oliverjames on 2012-08-21
Version 12.04, latest CUPS in the official repository.

---

### Post by pt123 on 2012-08-21
> **oliverjames said:**
> Version 12.04, latest CUPS in the official repository.

can you goto Synaptics and get the version, are you able to select all the text unlike what happened to me?

Would you be able to add a response to this in the bug report, it might help the maintainer solve by it's screwed up in Ubuntu 12.04

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820)

---

### Post by oliverjames on 2012-08-22
The version is 1.5.3-0ubuntu4, see attached image for all CUPS libs.

I'll try to post a bug report.

---

### Post by pvillela on 2013-03-12
I'm running 64 bit 12.04 and the Precise versionof cups-pdf (currently 2.6.1-6) generates images without selectable text.  I uninstalled that package and installed the Debian package directly from the cups-pdf site (version 2.5.0-16 [http://packages.debian.org/search?keywords=cups-pdf](http://packages.debian.org/search?keywords=cups-pdf)).  After running system-config-printer, cups-pdf is now working perfectly.

---

